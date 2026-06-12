---
title: "My New PHP WYSIWYG PDF library"
date: 2009-10-02
forum: Programming Talk
---

### Post by kstan_79 on 2009-10-02
Hi,

My company'd just develop an open source PHP report library which allow you design PDF report via Java based IReport report designer. When you run the report it will use FPDF library as foundation and convert ireport xml file to PDF on the fly.

We make use the FPDF library, you can increase the productivity 100%-300% if you know how to use iReport.

Since my company gain a lot of benefit from open source software, so we willing to contribute something to open source community.
This project is free to use and free to change, project name = PHPJasperXML.

Download at:
[http://www.simit.com.my/?q=phpjasperxml](http://www.simit.com.my/?q=phpjasperxml)

This is new library and we need you feed back. Please feed back at:
[http://www.extraknowledge.org/forum/viewforum.php?f=23](http://www.extraknowledge.org/forum/viewforum.php?f=23)

Below is the sample source code for display the report. Hopefully this project can spread fast, so that not PHP expert can design their PDF report easily.

Thanks for you trying this library.
Ks Tan



<?php

include_once('class/fpdf/fpdf.php');
include_once("class/PHPJasperXML.inc");
include_once ('setting.php'); //optional, just wanna to preset variable for database



$xml =  simplexml_load_file("sample1.jrxml");


$PHPJasperXML = new PHPJasperXML();
$PHPJasperXML->arrayParameter=array("parameter1"=>1);
$PHPJasperXML->xml_dismantle($xml);

$PHPJasperXML->transferDBtoArray($server,$user,$pass,$db);
$PHPJasperXML->outpage("I");    //page output method I:standard output  D:Download file


?>

---

