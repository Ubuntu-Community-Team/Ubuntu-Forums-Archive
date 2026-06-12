---
title: "JSON data rendering blues"
date: 2011-09-19
forum: Programming Talk
---

### Post by kunal00731 on 2011-09-19
Hi friends ,
this is a sticky issue .
Kindly advice.


I have a jsp file which gives me a template  return .
However there is a script which loads the JSON data for me.
Now when this script is embedded , all my data in head gets suppressed.

This is the source :
[COLOR=Magenta]
<%@ page language="java"contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>   
<html>
<head>
<title>Document Dashboard - Franklin Templeton</title>
<meta charset="utf-8">
<!-- Including the style sheets here . -->
<link rel="stylesheet" href="http://localhost:8080/springapp/css/jquery-ui-1.8.14.custom.css" type="text/css" />
<!-- Including the js files here . -->
<script type="text/javascript" src="http://localhost:8080/springapp/js/jquery-1.5.1.min.js">
</script>
<script type="text/javascript" src="http://localhost:8080/springapp/js/jquery-ui-1.8.14.custom.min.js">
</script>
<script type="text/javascript" src="http://localhost:8080/springapp/js/uki.dev.js">
</script>
<script type="text/javascript" src="http://localhost:8080/springapp/js/searchable.js">
</script>
<script type="text/javascript" src="http://localhost:8080/springapp/js/document.js">
</script>  
<script type='text/javascript'src='http://getfirebug.com/releases/lite/1.2/firebug-lite-compressed.js'>
</script>

<style type="text/css">
body {
font-size:11px;
}
#Tabs > div {
padding:0;
}
#DocTabs {
border:0;
}
.ui-tabs {
border:0;
}
input[type=text] {
padding:0.4em 1em 0.4em 0.3em;
border:1px solid #c5dbec;
}
#KIID > form input[type=text], #PilotModules > form input[type=text], #TranslationModules > form input[type=text] {
width:400px;
}
#Tabs > div {
padding:1em 1.4em;
}
#Tabs #Documents, #Tabs #Modules {
padding:0;
}
.funds_filter ul {
padding:0;
margin:0;
}
.funds_filter ul ul {
padding-left:2em;
list-style:none;
}
.rule {
padding:0.3em 1em 0.5em 0;
border-bottom:1px solid #a6C9e2;
margin:0 0 0.5em 0;
}
/*Filter Panels*/
#FilterTabs .ui-tabs-panel, #FiltersPilot .ui-tabs-panel, #FiltersTransaltion .ui-tabs-panel {
padding-right:0;
padding-left:0;
overflow-y:auto;
overflow-x:hidden;
max-height: 350px;
padding-bottom;
}
/*Filter Tab Dates*/
#FilterTabs .datefield {
padding:0.3em 0 0.5em;
}
#FilterTabs .datefield label {
margin-left:0.3em;
}
/*Get Data Dialog*/
#GetData {
margin-top:1em;
}
#GetDataTable {
min-height:400px;
}
/*Change Impact Panels*/
#ChangeImpactTabs .ui-tabs-panel {
padding-left:0;
padding-right:0;
padding-bottom:0;
}
#PilotTable {
min-height:365px;
}
</style>
<!-- Adding other styles here to make it renderable . -->
<style>
.uki-table-column-32 {width:489px;}
</style>
<style>
.uki-table-column-33 {width:89px;}
</style>
<style>
.uki-table-column-34 {width:89px;}
</style>
<style>
.uki-table-column-35 {width:89px;}
</style>
<style>
.uki-table-column-36 {width:89px;}
</style>
<style>
.uki-table-column-37 {width:89px;}
</style>
<style>
.uki-table-column-38 {width:89px;}
</style>
</head>
<!-- Body tag starts here. -->
<!-- Creating the first pane. Consists of Tasks,Documents,Modules.  -->
<body class="" style="">
<div id="Tabs" class="ui-tabs ui-widget ui-widget-content ui-corner-all">
<ul class="ui-tabs-nav ui-helper-reset ui-helper-clearfix ui-widget-header ui-corner-all">
<li class="ui-state-default ui-corner-top ui-state-disabled">
<a href="#">
<span>Tasks</span>
</a>
</li>
<li class="ui-state-default ui-corner-top ui-tabs-selected ui-state-active">
<a href="#Documents">
<span>Documents</span>
</a>
</li>
<li class="ui-state-default ui-corner-top ui-state-disabled">
<a href="#">
<span>Modules</span>
</a>
</li>
</ul>
<!-- Creating the second pane. Consists of KIID,PIB,Commentry. -->
<div id="Documents" class="ui-tabs-panel ui-widget-content ui-corner-bottom">
<div id="DocTabs" class="ui-tabs ui-widget ui-widget-content ui-corner-all">
<ul class="ui-tabs-nav ui-helper-reset ui-helper-clearfix ui-widget-header ui-corner-all">
<li class="ui-state-default ui-corner-top ui-tabs-selected ui-state-active">
<a href="#KIID">
<span>KIID</span>
</a>
</li>
<li class="ui-state-default ui-corner-top ui-state-disabled">
<a href="#">
<span>PIB</span>
</a>
</li>
<li class="ui-state-default ui-corner-top ui-state-disabled">
<a href="#">
<span>Commentry</span>
</a>
</li>
</ul>
<div id="KIID" class="ui-tabs-panel ui-widget-content ui-corner-bottom">
<form action="">
<div>
<label for="FindDoc">Find</label>
<input id="FindDoc" type="text">
<button class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" type="submit" role="button" aria-disabled="false">
<span class="ui-button-text">Search</span>
</button>
<button id="FilterBy" class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" role="button" aria-disabled="false">
<span class="ui-button-text">Filter By</span>
</button>
</div>
</form>
<div style="padding:1em 0;">
<div style="width:50%;display:inline-block;">
<button class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" role="button" aria-disabled="false">
<span class="ui-button-text">Generate</span>
</button>
<button id="GetLatestData" class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" role="button" aria-disabled="false">
<span class="ui-button-text">Get Latest Data</span>
</button>
</div>
<div style="width:49%;display:inline-block">
<button class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" role="button" aria-disabled="false">
<span class="ui-button-text">Approve</span>
</button>
<button class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" role="button" aria-disabled="false">
<span class="ui-button-text">Sent To Review</span>
</button>
<button class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" role="button" aria-disabled="false">
<span class="ui-button-text">Publish</span>
</button>
<button class="ui-button ui-widget ui-state-default ui-corner-all ui-button-text-only" role="button" aria-disabled="false">
<span class="ui-button-text">Download</span>
</button>
</div>
</div>
</div>
</div>
</div>
</div>
<!-- Doing the JSON Loading here .  -->
<script type="text/javascript">
    
    //Setup Main Tabs
$(function() {
    $("#Tabs").tabs({
        ajaxOptions: {
            error: function( xhr, status, index, anchor ) {
                $(anchor.hash).html("No AJAX response.");
            }
        },
        selected: 1
    });
});

//Setup Document Tabs
$(function() {
    $("#DocTabs").tabs({
        ajaxOptions: {
            error: function( xhr, status, index, anchor ) {
                $(anchor.hash).html("No AJAX response.");
            }
        }
    });
});

//Table UKI
uki(
    {
        view: 'Table',
        rect: '1000 1000',
        anchors: 'left right top bottom',
        columns: [
            { view: 'table.CustomColumn', label: 'Working Document', sort: 'ASC', resizable: true, width:500},
            { view: 'table.NumberColumn', label: 'Status', resizable: true, formatter: formatStatus },
            { view: 'table.CustomColumn', label: 'Data Received', resizable: true, formatter: formatDate },
            { view: 'table.CustomColumn', label: 'Generated PDF', resizable: true, formatter: formatDate },
            { view: 'table.NumberColumn', label: 'Status', resizable: true, formatter: formatStatus },
            { view: 'table.CustomColumn', label: 'Date Published', resizable: true, formatter: formatDate },
            { view: 'table.CustomColumn', label: 'Date Expired', resizable: true, formatter: formatDate }
        ],
        multiselect: true,
        style: {fontSize: '11px', lineHeight: '11px'}
    }
).attachTo(document.getElementById("DocsTable"), '1000 1000');

// Custom Status
function formatStatus(t) {
    switch(t) {
        case "1":
            return '<span style="color:green;font-size:22px">&bull;</span>';
            break;
        case "2":
            return 'Pending';
            break;
        case "3":
            m = "Mar"
            break;
        case "4":
            m = "Apr"
            break;
        case "5":
            m = "May";
            break;
        case "6":
            m = "Jun"
            break;
        case "7":
            m = "Jul"
            break;
        case "8":
            m = "Aug"
            break;
        case "9":
            m = "Sep";
            break;
        case "10":
            m = "Oct"
            break;
        default:
            break;                        
    }    
}

//Custom Date
function formatDate(t) {
    var m;
    switch(t.substring(0,2)) {
        case "01":
            m = "Jan";
            break;
        case "02":
            m = "Feb"
            break;
        case "03":
            m = "Mar"
            break;
        case "04":
            m = "Apr"
            break;
        case "05":
            m = "May";
            break;
        case "06":
            m = "Jun"
            break;
        case "07":
            m = "Jul"
            break;
        case "08":
            m = "Aug"
            break;
        case "09":
            m = "Sep";
            break;
        case "10":
            m = "Oct"
            break;
        case "11":
            m = "Nov"
            break;
        case "12":
            m = "Dec"
            break;
        default:
            break;                    
    }    
    return t.substring(2,4)+" "+m+" 20"+t.substring(4,6);
}

//UKI Search
window.DummyModel = uki.newClass(Searchable, new function() {
    this.init = function(data) {
        this.items = data;
        uki.each(this.items, function(i, row) {
            row.searchIndex = row[0].toLowerCase();
        })
    };
    
    this.matchRow = function(row, iterator) {
        return row.searchIndex.indexOf(iterator.query) > -1;
    };
});

//UKI Load
window.onLibraryLoad = function(data) {
    alert('hi');
    $("#DocNumber").html("<strong>"+data.length+"</strong> Loaded Documents");
    var model = new DummyModel(data),
        lastQuery = '',
        table = uki('Table');
        
    model.bind('search.foundInChunk', function(chunk) {
        table.data(table.data().concat(chunk)).layout();
    });
    
    table.find('Header').bind('columnClick', function(e) {
        var header = this;
            
        if (e.column.sort() == 'ASC') e.column.sort('DESC');
        else e.column.sort('ASC');
        
        header.redrawColumn(e.columnIndex);
        uki.each(header.columns(), function(i, col) {
            if (col != e.column && col.sort()) {
                col.sort('');
                header.redrawColumn(i);
            }
        });
        model.items = e.column.sortData(model.items);
        table.data(model.items);
    })
    
    table.data(model.items);
    
    //JQuery UKI Filter
    $("#FindDoc").bind("click keyup",function() {    
        if (this.value.toLowerCase() == lastQuery) return;
        lastQuery = this.value.toLowerCase();
        if (lastQuery.match(/\S/)) {
            hlt = lastQuery;
            table.data([]);
            model.search(lastQuery);
        } else {
            hlt = '';
            table.data(model.items);
        }
    });
    document.body.className += '';
};

var script = document.createElement('script'),
    head = document.getElementsByTagName('head')[0];
    script.src = "http://localhost:8080/springapp/js/God.js";    
    head.insertBefore(script, head.firstChild);

</script>

</body>
</html>


[COLOR=Black]Now the problem is the data gets loaded, but the  portion inside the head part does not come up.

Kindly help me out here. [/COLOR]


[/COLOR]

---

### Post by kunal00731 on 2011-09-20
Hi , perhaps I should explicitly tell my problem.  
I am still at my wits end and could not find any solution till now. Kindly help, plz.

I have a CSS file which describes the lay out . Also I have a jsp file which renders  JSON data  and shows it in a web page. Now i am seeing  a completely new kind of a problem. If the project can be divided into two parts, I will say that the first part is 1st.jsp, which shows some buttons  and tabs. 2nd.jsp shows JSON data . When i combine  the code in both the files, only content of 2nd.jsp comes out. However if i scroll that content, i get a glimpse of the content of 1st.jsp   in the background.

Why is this happening kindly help.

---

### Post by slavik on 2011-09-20
1. making html pink and outside of code tags helps a lot, thanks.
2. are you sure there is not styling issue? how about looking at the html sopurce that the jsp produces, does it have the json data?

---

