---
title: "PHP Internet Explorer Issue"
date: 2012-02-11
forum: Programming Talk
---

### Post by Anstice on 2012-02-11
Hi guys,

I have a site that uses XML, PHP, JSON, and DOM to display xml info in a table when it is selected from a dropdown box. Javascript calls a php file to get the data when the file is selected in the dropdown box and this all works fine. 

The issue I have is when adding an entry to the XML, it is fully implemented in Chrome and Firefox but doesn't work in Internet Explorer. It will append to the XML but will not show the new entries unless the page is opened in a new tab, refreshing doesn;t work.

I have checked and it doesn't seem to be a caching issue as I have implemented both the cache_control and randomstr solution to make sure each request is unique. I've included the code below for getting the data and decoding the JSON string. Anyone have any ideas?

Gets the XML:
```

<?php

  ini_set('display_errors',1); 
  error_reporting(E_ALL);

  /* gets the selected file to use to return data */
  $xml_filename = './XML/'.$_REQUEST['file'];
  $xml = simplexml_load_file($xml_filename);

  /* gets the root of the selected file */
  $rootname = $xml->getName();
  /* gets the children in that root */
  $children = $xml->children();
  $firstchild = $children[0];

  // gets the table headings
  $data = '{"headings":[';
  foreach ($firstchild as $elem)
  {
    $data = $data.'"'.$elem->getName().'",';
  }

  // removes trailing ','
  $data = substr_replace($data,"",-1);
  $data = $data.'],';

  // gets the cell values
  $data = $data. '"vals":[';
  foreach ($children as $child)
  {
    $data = $data.'[';
    foreach ($child as $elem => $vals)
    {
      $data = $data.'"'.$vals.'",';
    }
    $data = substr_replace($data,"",-1);
    $data = $data.'],';
  }

  // removes trailing ','
  $data = substr_replace($data,"",-1);
  $data = $data.']}';

  /* sends created JSON string back to client */
  echo $data;

?>

```

Decoding and putting into table:
```

$(document).ready(function()
  {
  $("#list1").jCombo("getXMLFilenames.php", {});
  $("#list1").change(function()
  {
    if($("#list1").val() == 0)
    {
      /* form hidden until file is chosen */
      $("#input").hide();
    }
    else
    {
      $("#input").show();
      /* gets the information from the server side, creates
         the table, and fills it with the data */
      $("p").html("");
      $.getJSON('getData.php?file='+($('#list1').val()), function(data)
      {
        /* opens the table, sets the width and padding */
        var html = "<table width=90% cellpadding=5><tr>";
	/* gets the no. of columns and rows using data */
	var cols = data.headings.length;
	var rows = data.vals.length;
		
	var x = 0;
	/* creates the headings from data */
	for (x=0; x<cols; x++)
	{
	  /* creates each header cell */
	  html = html + "<th>" + data.headings[x] + "</th>";
        }
	/* closes the heading row */
	html = html + '</tr>';
	/* counts the cells that will be needed to hold data */
	var colData = data.headings.length;
	var y = 0;
	/* creates and fills the cells */
	for (y=0;y<rows;y++)
	{
	  /* opens the row */
	  html = html + "<tr>";
          for (x=0; x<colData; x++)
	  {
	    /* puts each value in it's cell row by row */
	    html = html + "<td>" + data.vals[y][x] + "</td>";
	  }
	  html = html + "</tr>";
        }
	/* closes the table */
	html = html + "</table>";
	$("p").html(html);
	/* returns the built up var to create the table in <tab> */
	return html;
	});
  }

```

---

