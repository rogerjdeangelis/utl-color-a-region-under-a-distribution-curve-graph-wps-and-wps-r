# utl-color-a-region-under-a-distribution-curve-graph-wps-and-wps-r
Color a region under a distribution curve graph wps and wps r 
    %let pgm=utl-color-a-region-under-a-distribution-curve-graph-wps-and-wps-r;

    Color a region under a distribution curve graph wps and wps r

    github graph
    http://tinyurl.com/ncsw8phj
    https://github.com/rogerjdeangelis/utl-color-a-region-under-a-distribution-curve-graph-wps-and-wps-r/blob/main/beta.pdf

    github
    http://tinyurl.com/m5rx577b
    https://github.com/rogerjdeangelis/utl-color-a-region-under-a-distribution-curve-graph-wps-and-wps-r

    related repos on end

    /*               _     _
     _ __  _ __ ___ | |__ | | ___ _ __ ___
    | `_ \| `__/ _ \| `_ \| |/ _ \ `_ ` _ \
    | |_) | | | (_) | |_) | |  __/ | | | | |
    | .__/|_|  \___/|_.__/|_|\___|_| |_| |_|
    |_|
    */

    /**************************************************************************************************************************/
    /*                             |                                     |                                                    */
    /*     INPUT                   |       PROCESS                       |                   OUTPUT                           */
    /*                             |                                     |                                                    */
    /*                             |                                     |     0.0       0.2       0.4       0.6       0.8    */
    /* %let density    = dbeta    ;|ggplot(data.frame(x = 0:1), aes(x))+ |   ---+---------+---------+---------+---------+--   */
    /* %let parameters = %str(2,5);|  stat_function(fun = &density,      | Y |                                            |   */
    /* %let x_lower    = 0.05     ;|  args = c(&parameters),geom ='area',| 3 +                                            + 3 */
    /* %let x_higher   = 0.35     ;|  xlim = c(&x_lower, &x_higher),     |   |          ****                              |   */
    /* %let pdf        = beta.pdf ;|  fill = 'yellow') +                 |   |         *******                            |   */
    /*                             |   stat_function(fun = &density,     |   |        ***#####*                           |   */
    /*                             |   args = c(&parameters));           | 2 +       **#######**                          + 2 */
    /*                             |                                     |   |       *######### *                         |   */
    /*                             |                                     |   |      * #########  *                        |   */
    /*                             |                                     |   |      * #########   *                       |   */
    /*                             |                                     |   |     *  #########    **                     |   */
    /*                             |                                     |   |     *  #########     **                    |   */
    /*                             |                                     |   |        #########      **                   |   */
    /*                             |                                     | 1 +    *   #########       **                  + 1 */
    /*                             |                                     |   |    *   #########         *                 |   */
    /*                             |                                     |   |        #########          **               |   */
    /*                             |                                     |   |   *    #########           ***             |   */
    /*                             |                                     |   |        #########             **            |   */
    /*                             |                                     |   |   *    #########               ***         |   */
    /*                             |                                     |   |        #########                 *****     |   */
    /*                             |                                     | 0 +  *     #########                  *********+ 0 */
    /*                             |                                     |   |        #########                           |   */
    /*                             |                                     |   ---+---------+---------+---------+---------+--   */
    /*                             |                                     |     0.0       0.2       0.4       0.6       0.8    */
    /*                             |                                     |                          X                         */
    /*                             |                                     |                                                    */
    /**************************************************************************************************************************/

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */


     %let density    = dbeta    ;
     %let parameters = %str(2,5);
     %let x_lower    = 0.05     ;
     %let x_higher   = 0.35     ;
     %let pdf        = d:/pdf/beta.pdf ;


    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    %utlfkil(d:/pdf/beta.pdf);

    %utl_submit_wps64x("

         %let density    = dbeta             ;
         %let parameters = %str(2,5)         ;
         %let x_lower    = 0.05              ;
         %let x_higher   = 0.35              ;
         %let pdf        =  d:/pdf/beta.pdf  ;

         proc r;

         submit;
          library(ggplot2);
          pdf('&pdf');
          ggplot(data.frame(x = 0:1), aes(x)) +
            stat_function(fun = &density, args = c(&parameters), geom = 'area',
            xlim = c(&x_lower, &x_higher), fill = 'yellow') +
            stat_function(fun = &density, args = c(&parameters));
          endsubmit;

         run;quit;

    ");

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */


    /**************************************************************************************************************************/
    /*|                                                                                                                       */
    /*|                   OUTPUT                                                                                              */
    /*|                                                                                                                       */
    /*|     0.0       0.2       0.4       0.6       0.8                                                                       */
    /*|   ---+---------+---------+---------+---------+--                                                                      */
    /*| Y |                                            |                                                                      */
    /*| 3 +                                            + 3                                                                    */
    /*|   |          ****                              |                                                                      */
    /*|   |         *******                            |                                                                      */
    /*|   |        ***#####*                           |                                                                      */
    /*| 2 +       **#######**                          + 2                                                                    */
    /*|   |       *######### *                         |                                                                      */
    /*|   |      * #########  *                        |                                                                      */
    /*|   |      * #########   *                       |                                                                      */
    /*|   |     *  #########    **                     |                                                                      */
    /*|   |     *  #########     **                    |                                                                      */
    /*|   |        #########      **                   |                                                                      */
    /*| 1 +    *   #########       **                  + 1                                                                    */
    /*|   |    *   #########         *                 |                                                                      */
    /*|   |        #########          **               |                                                                      */
    /*|   |   *    #########           ***             |                                                                      */
    /*|   |        #########             **            |                                                                      */
    /*|   |   *    #########               ***         |                                                                      */
    /*|   |        #########                 *****     |                                                                      */
    /*| 0 +  *     #########                  *********+ 0                                                                    */
    /*|   |        #########                           |                                                                      */
    /*|   ---+---------+---------+---------+---------+--                                                                      */
    /*|     0.0       0.2       0.4       0.6       0.8                                                                       */
    /*|                          X                                                                                            */
    /*|                                                                                                                       */
    /**************************************************************************************************************************/



    REPO
    --------------------------------------------------------------------------------------------------------------------------------------
    https://github.com/rogerjdeangelis/utl-Create-a-side-by-side-table-and-graph-using-greplay
    https://github.com/rogerjdeangelis/utl-Graph-with-known-intercept-and-slope
    https://github.com/rogerjdeangelis/utl-Graphics-Surveying-ten-random-locations-in-North-Carolina-using-superinposed-grid
    https://github.com/rogerjdeangelis/utl-NHANES-full-raw-demographic-and-health-data-R-Package
    https://github.com/rogerjdeangelis/utl-R-AI-igraph-list-connections-in-a-non-directed-graph-for-a-subset-of-vertices
    https://github.com/rogerjdeangelis/utl-adding-text-to-an-existing-png-graphic-python-AI
    https://github.com/rogerjdeangelis/utl-changepoint-like-analysis-in-R-and-SAS-elbow-graph
    https://github.com/rogerjdeangelis/utl-classic-sas-and-well-designed-tables-and-ascii-graphics-instead-of-bling
    https://github.com/rogerjdeangelis/utl-create-graphs-in-excel-using-excel-chart-templates
    https://github.com/rogerjdeangelis/utl-creating-a-clinical-demographic-report-using-r-and-python-sql
    https://github.com/rogerjdeangelis/utl-dygraph-javascript-library-from-MIT
    https://github.com/rogerjdeangelis/utl-excel-report-with-two-side-by-side-graphs-below_python
    https://github.com/rogerjdeangelis/utl-graphics-boxplots-with-jiggled-point-values-alongside
    https://github.com/rogerjdeangelis/utl-how-many-triangles-in-the-polygon-r-igraph-AI
    https://github.com/rogerjdeangelis/utl-identical-side-by-side-text-and-graphics-in-pdf-and-powerpoint
    https://github.com/rogerjdeangelis/utl-identify-linked-and-unliked-paths-r-igraph
    https://github.com/rogerjdeangelis/utl-igraph-find-largest-group-of-unrelated-individuals-in-your-family-reunion
    https://github.com/rogerjdeangelis/utl-make-fake-relational-clinical-tables-demographics-lab-exposure-adverse-events
    https://github.com/rogerjdeangelis/utl-quality-graphics-in-R-wps-and-sas
    https://github.com/rogerjdeangelis/utl-r-graphics-vs-wps-base-graphics-layering-in-r-versus-procs-in-wps-base-ggplot2
    https://github.com/rogerjdeangelis/utl-shortest-and-longest-travel-time-from-home-to-work-igraph-AI
    https://github.com/rogerjdeangelis/utl-under-used-proc-calendar-ascii-graphics
    https://github.com/rogerjdeangelis/utl_R_graphics_polar_plot
    https://github.com/rogerjdeangelis/utl_adding_SAS_graphics_at_an_arbitrary_position_into_existing_excel_sheets
    https://github.com/rogerjdeangelis/utl_classic_sas_graph_greplay_harvard_macro_multiple_plots_per_page
    https://github.com/rogerjdeangelis/utl_classic_sas_graph_three_plots_across_many_methods_long_live
    https://github.com/rogerjdeangelis/utl_custom_graphics_in_R
    https://github.com/rogerjdeangelis/utl_download_2015_ACS_5yr_zipcode_level_american_community_survey_demographics_as_sas_dataset
    https://github.com/rogerjdeangelis/utl_fun_with_line_printer_graphics_editor
    https://github.com/rogerjdeangelis/utl_graph_visualize_crosstab
    https://github.com/rogerjdeangelis/utl_graphics_589_SAS_and_R_graphics_with_code_and_datasets
    https://github.com/rogerjdeangelis/utl_graphics_determine_us_state_from_latitude_and_longitude
    https://github.com/rogerjdeangelis/utl_graphics_fit_a_smooth_line_to_a_scatter_plot_loess
    https://github.com/rogerjdeangelis/utl_graphics_flexibility_of_ascii_bar_charts
    https://github.com/rogerjdeangelis/utl_graphics_plotting_rivers_in_brazil_using_sharpefiles
    https://github.com/rogerjdeangelis/utl_graphics_zipcode_boundary_maps
    https://github.com/rogerjdeangelis/utl_how_to_stack_a_table_and_corresponding_bar_graph
    https://github.com/rogerjdeangelis/utl_javascript_and_classic_map_graphics_with_mouseovers_and_multiple_drilldowns
    https://github.com/rogerjdeangelis/utl_javascript_dygraph_graphics_multipanel_time_series
    https://github.com/rogerjdeangelis/utl_minimal_code_for_demographic_clinical_n_percent_report
    https://github.com/rogerjdeangelis/utl_pdf_graphics_top_40_a_sas_ods_graphics_look_at_chicago_public_schools_salaries_by_job
    https://github.com/rogerjdeangelis/utl_polar_graphics_pot_violin_plot
    https://github.com/rogerjdeangelis/utl_proc_gmap_classic_graphics_grid_containing_four_states
    https://github.com/rogerjdeangelis/utl_r_graphics_visualizing_assciation_amoung_many_variables
    https://github.com/rogerjdeangelis/utl_remove_isolated_nodes_from_an_network_r_igraph
    https://github.com/rogerjdeangelis/utl_sas_classic_graphics_15_plots_on_a_page
    https://github.com/rogerjdeangelis/utl_sas_classic_graphics_designing_your_greplay_template
    https://github.com/rogerjdeangelis/utl_sas_classic_graphics_grid_of__proc_univariate_histograms
    https://github.com/rogerjdeangelis/utl_sas_classic_graphs_using_phil_mason_grid_macro_for_layout
    https://github.com/rogerjdeangelis/utl_table_graph_ppt
    https://github.com/rogerjdeangelis/utl_wps_sas_classic_graphics_optimum_minimums_maximums_increments_for-axes


    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
