<html>
  <head>
    <!--Load the AJAX API-->
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
    <script type="text/javascript">

      function drawVisualization() {
        var query = new google.visualization.Query(
        'https://docs.google.com/spreadsheets/d/1l85EUiUORYHqsen_0_GztVN0XdDPk-6G5XuVBeWXSFE/edit?usp=sharing');

          // Apply query language statement.
          query.setQuery('SELECT A,B');

          // Send the query with a callback function.
          query.send(handleQueryResponse);
        }

        function handleQueryResponse(response) {
          if (response.isError()) {
            alert('Error in query: ' + response.getMessage() + ' ' + response.getDetailedMessage());
            return;
          }

          var data = response.getDataTable();
          visualization = new google.visualization.PieChart(document.getElementById('visualization'));
          visualization.draw(data, {legend: 'bottom'});
        }
    </script>
  </head>

  <body>
    <!--Div that will hold the pie chart-->
    <div id="chart_div"></div>
  </body>
</html>
