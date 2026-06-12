---
title: "Thumbnail Galleries with javascript"
date: 2007-12-30
forum: Programming Talk
---

### Post by neleininger on 2007-12-30
I want to thank anyone who takes the time to read this ahead of time i think it is a in depth problem and very specific to my code.

I have designed this gallery that loads up thumbnails of the pictures and all of this is based on a JavaScript file created by Photoshop CS3 that look like this:

WPGgallery = new Object();
WPGgallery.name = "2007_12_24_First";
WPGgallery.photographer = "Nick%20Leininger";
WPGgallery.contact = "";
WPGgallery.email = "";
WPGgallery.date = "12/28/07"

WPGgallery.colors = new Object();
WPGgallery.colors.background = "#000000";
WPGgallery.colors.banner = "#F0F0F0";
WPGgallery.colors.text = "#000000";
WPGgallery.colors.link = "#0000FF";
WPGgallery.colors.alink = "#FF0000";
WPGgallery.colors.vlink = "#800080";

gPhotos = new Array();
gPhotos[0] = new Object();
gPhotos[0].filename = "IMG_3198.jpg";
gPhotos[0].ImageWidth = 600;
gPhotos[0].ImageHeight = 450;
gPhotos[0].ThumbWidth = 150;
gPhotos[0].ThumbHeight = 112;
gPhotos[0].meta = new Object();

gPhotos[1] = new Object();
gPhotos[1].filename = "IMG_3199.jpg";
gPhotos[1].ImageWidth = 450;
gPhotos[1].ImageHeight = 600;
gPhotos[1].ThumbWidth = 112;
gPhotos[1].ThumbHeight = 150;
gPhotos[1].meta = new Object();

gPhotos[2] = new Object();
gPhotos[2].filename = "IMG_3200.jpg";
gPhotos[2].ImageWidth = 450;
gPhotos[2].ImageHeight = 600;
gPhotos[2].ThumbWidth = 112;
gPhotos[2].ThumbHeight = 150;
gPhotos[2].meta = new Object();

and it continues on for as many pictures as there are in the gallery. the problem comes about in every gallery there is this file called photos.js and they all contain the same script and create the same array gPhotos. my code takes advantage of this but falls apart when i try to switch between different galleries. that is load up a different version of gPhotos associated with a new gallery. My code is as follows (its rather long):

The problem spots are highlighted in red. GalTable creates a table of all of the available galleries with a thumbnail of the first photos as the link. Thumbtalbe creates the whole Gallery selected from the previous table. The problem is everytime i try to replace gPhotos the new one will not load. I can confirm that the js file being referenced has changed but it will not reload the gPhotos array at that time, which is critical for this code to work.

Again thank you for taking a look at this and I appreciate any input. I am alright with programming and can feel my way around but an no where near an expert so I would not be surprised if my code is breaking some huge rules. But it does work aside from the mentioned problem

function GalTable(List, page)
{

var numPP = 25; //number of pictures per page
var rowlen = 5; //picture per row
var numpic = 0; //pictures to be displayed on page assigned later
var pics = List.length; //number of pictures in the gallery
var firstpic = (page - 1) * 25; //where to start in the List array
var totpic = pics - firstpic; //pictures left after current page
var whole = pics % numPP; //tell if last page fills completely
var pages = pics / numPP; //number of full pages
var totpage = 0; //total number of papges
var maxwidth = "150"; //constant variable in the Table
var index = ""; //string to hold the links to the other pages

if(totpic >= numPP) //assign the number of pictures on the page
numpic = numPP;
else
numpic = totpic;

if(whole == 0) //assign the total nummber of pages
totpage = pagse;
else
totpage = pages + 1;

for(x = 1; x <= totpage; x++) //create the links to all of the other pages
{
if(x == page)
index = index + "|Page - " + x.toString() + "|";
else
index = index + "|<A HREF=\"javascript:GalTable(\'" + Gallery + "\'," + x.toString() + ")\">Page - " + x.toString() + "</A>|";
}

for(g = 0; g < numPP; g++) //build the talbe for the current page
{
if(g % rowlen == 0 && g > 0) //create a new row every time the limit of pcitures per row is met
{
Table = Table + "</tr><tr>";
}

if(g == 0) //set up the fits cell and row and table
{
//gPhotos = null;
[COLOR="Red"]replaceFile(document.getElementById("piclist").getAttribute("src"),List[0] + "/photos.js","js");//switches galleries to load the first image from each gallery[/COLOR]

Table = "<table width=\"780\"><tr><td align=\"center\"> Public Galleries </td></tr><tr><td align=\"center\">" + index + "</td></tr></table>" +
"<table><tr>" +
"<td align=\"middle\"><table cellpadding=0 cellspacing=0 border=0 bgcolor=\"#000000\" width=\"" + maxwidth + "\"><tr><td valign=\"top\" align=\"center\"><A HREF=\"javascript:ThumbTable(\'" + List[g] + "\',1)\"><IMG src=\"" + List[g] + "/thumbnails/" + gPhotos[0].filename + "\" height=\"" + gPhotos[0].ThumbHeight.toString() + "\" width=\"" + gPhotos[0].ThumbWidth.toString() + "\" border=1 style=\"border:1pt solid white\" alt=\"" + gPhotos[0].filename + "\"></A><BR></td></tr></table></td>";
}

if(g > 0 && g < numpic) // adds the rest of the pictures into the table
{
//gPhotos = null;
[COLOR="Red"]replaceFile(List[g - 1] + "/photos.js",List[g] + "/photos.js","js"); //switches galleries to load the first image from each gallery
alert(document.getElementById("piclist").getAttribute("src")) //confirms that new file has been loaded butthe new gPhotos array is not loaded at this time
// ^^^^PROBLEM!!!!!^^^^ occurs with every call of repalceFile defined below[/COLOR]
Table = Table +
"<td align=\"middle\"><table cellpadding=0 cellspacing=0 border=0 bgcolor=\"#000000\" width=\"" + maxwidth + "\"><tr><td valign=\"top\" align=\"center\"><A HREF=\"javascript:ThumbTable(\'" + List[g] + "\',1)\"><IMG src=\"" + List[g] + "/thumbnails/" + gPhotos[0].filename + "\" height=\"" + gPhotos[0].ThumbHeight.toString() + "\" width=\"" + gPhotos[0].ThumbWidth.toString() + "\" border=1 style=\"border:1pt solid white\" alt=\"" + gPhotos[0].filename + "\"></A><BR></td></tr></table></td>";
}

if(g == (numPP - 1)) //closes the table
{
Table = Table +
"</tr></table>" +
"<table width=\"780\"><tr><td align=\"center\">" + index + "</td></tr></table>";
}

if(g >= numpic && g < (numPP - 1)) //fills in blank spots for a partially full page
{
Table = Table +
"<td align=\"center\" valign=\"center\">&nbsp; </td>";
}

}
document.body.innerHTML = Table; //writes the table to the body of the webpage
gPhotos = null; //clears gPhotos
}


function ThumbTable(Gallery, page)
{
[COLOR="Red"]replaceFile(document.getElementById("piclist").getAttribute("src"),Gallery + "/photos.js","js"); //loads the list of pictures to be displayed
//a file created by photoshop CS3[/COLOR]
var numPP = 25; //number of pictures per page
var rowlen = 5; //picture per row
var numpic = 0; //pictures to be displayed on page assigned later
var pics = gPhotos.length; //number of pictures in the gallery
var firstpic = (page - 1) * 25; //where to start in the List array
var totpic = pics - firstpic; //pictures left after current page
var whole = pics % numPP; //tell if last page fills completely
var pages = pics / numPP; //number of full pages
var totpage = 0; //total number of papges
var maxwidth = "150"; //constant variable in the Table
var index = ""; //string to hold the links to the other pages

if(totpic >= numPP) //assign the number of pictures on the page
numpic = numPP;
else
numpic = totpic;

if(whole == 0) //assign the total nummber of pages
totpage = pagse;
else
totpage = pages + 1;

Home = "|<A HREF=\"javascript:GalTable(gList,1)\"> Gallery Home </A>|"; //link to get back to the gallery main page

for(x = 1; x <= totpage; x++) //create the links to all of the other pages
{
if(x == page)
index = index + "|Page - " + x.toString() + "|";
else
index = index + "|<A HREF=\"javascript:ThumbTable(\'" + Gallery + "\'," + x.toString() + ")\">Page - " + x.toString() + "</A>|";
}

for(g = 0; g < numPP; g++) //build the talbe
{
if(g % rowlen == 0 && g > 0) //create a new row everytime the limit of picture per row is reached
{
Table = Table + "</tr><tr>";
}

if(g == 0) //set up the main talbe the first row and cell along with all of the links
{
Table = "<table width=\"780\"><tr><td align=\"center\">" + Gallery +"</td></tr><tr><td align=\"center\">" + index + "</td></tr><tr><td align=\"center\">" + Home +"</td></tr></table>" +
"<table><tr>" +
"<td align=\"middle\"><table cellpadding=0 cellspacing=0 border=0 bgcolor=\"#000000\" width=\"" + maxwidth + "\"><tr><td valign=\"top\" align=\"center\"><IMG src=\"" + Gallery + "/thumbnails/" + gPhotos[g + firstpic].filename + "\" height=\"" + gPhotos[g + firstpic].ThumbHeight.toString() + "\" width=\"" + gPhotos[g + firstpic].ThumbWidth.toString() + "\" border=1 style=\"border:1pt solid white\" alt=\"" + gPhotos[g + firstpic].filename + "\" pbsrc=\"" + Gallery + "/images/" + gPhotos[g + firstpic].filename + "\" class=\"PopBoxImageSmall\" title=" + gPhotos[g + firstpic].filename + " onclick=\"Pop(this,50,'PopBoxImageLarge');\"><BR></td></tr></table></td>";
}

if(g > 0 && g < numpic) //add all of the pictures to the cell
{
Table = Table +
"<td align=\"middle\"><table cellpadding=0 cellspacing=0 border=0 bgcolor=\"#000000\" width=\"" + maxwidth + "\"><tr><td valign=\"top\" align=\"center\"><IMG src=\"" + Gallery + "/thumbnails/" + gPhotos[g + firstpic].filename + "\" height=\"" + gPhotos[g + firstpic].ThumbHeight.toString() + "\" width=\"" + gPhotos[g + firstpic].ThumbWidth.toString() + "\" border=1 style=\"border:1pt solid white\" alt=\"" + gPhotos[g + firstpic].filename + "\" pbsrc=\"" + Gallery + "/images/" + gPhotos[g + firstpic].filename + "\" class=\"PopBoxImageSmall\" title=" + gPhotos[g + firstpic].filename + " onclick=\"Pop(this,50,'PopBoxImageLarge');\"><BR></td></tr></table></td>";
}

if(g == (numPP - 1)) //close the talbe
{
Table = Table +
"</tr></table>" +
"<table width=\"780\"><tr><td align=\"center\">" + index + "</td></tr><tr><td align=\"center\">" + Home +"</td></tr></table>";
}

if(g >= numpic && g < (numPP - 1)) //fill in blank space for partially full page
{
Table = Table +
"<td align=\"center\" valign=\"center\">&nbsp; </td>";
}
}
document.body.innerHTML = Table; //writes the table to the body of the current html document
gPhotos = null; //clears gPhotos
}

//the following function will load replace and remove a javascript file or css file on demand
function loadFile(filename, filetype){
if (filetype=="js"){ //if filename is a external JavaScript file
var fileref=document.createElement('script')
fileref.setAttribute("language","JavaScript")
fileref.setAttribute("type","text/javascript")
fileref.setAttribute("id","piclist")
fileref.setAttribute("src", filename)
}
else if (filetype=="css"){ //if filename is an external CSS file
var fileref=document.createElement("link")
fileref.setAttribute("rel", "stylesheet")
fileref.setAttribute("type", "text/css")
fileref.setAttribute("href", filename)
}
if (typeof fileref!="undefined"){
document.getElementsByTagName("head").item(0).appendChild(fileref)
}
}

function removeFile(filename, filetype){
var targetelement=(filetype=="js")? "script" : (filetype=="css")? "link" : "none" //determine element type to create nodelist from
var targetattr=(filetype=="js")? "src" : (filetype=="css")? "href" : "none" //determine corresponding attribute to test for
var allsuspects=document.getElementsByTagName(targetelement)
for (var i=allsuspects.length; i>=0; i--){ //search backwards within nodelist for matching elements to remove
if (allsuspects[i] && allsuspects[i].getAttribute(targetattr)!=null && allsuspects[i].getAttribute(targetattr).indexOf(filename)!=-1)
allsuspects[i].parentNode.removeChild(allsuspects[i]) //remove element by calling parentNode.removeChild()
}
}
[COLOR="Red"]
function createFile(filename, filetype){
if (filetype=="js"){ //if filename is a external JavaScript file
var fileref=document.createElement('script')
fileref.setAttribute("language","JavaScript")
fileref.setAttribute("type","text/javascript")
fileref.setAttribute("id","piclist")
fileref.setAttribute("src", filename)
}
else if (filetype=="css"){ //if filename is an external CSS file
var fileref=document.createElement("link")
fileref.setAttribute("rel", "stylesheet")
fileref.setAttribute("type", "text/css")
fileref.setAttribute("href", filename)
}
return fileref
}

function replaceFile(oldfilename, newfilename, filetype){
var targetelement=(filetype=="js")? "script" : (filetype=="css")? "link" : "none" //determine element type to create nodelist using
var targetattr=(filetype=="js")? "src" : (filetype=="css")? "href" : "none" //determine corresponding attribute to test for
var allsuspects=document.getElementsByTagName(targetelement)
for (var i=allsuspects.length; i>=0; i--){ //search backwards within nodelist for matching elements to remove
if (allsuspects[i] && allsuspects[i].getAttribute(targetattr)!=null && allsuspects[i].getAttribute(targetattr).indexOf(oldfilename)!=-1){
var newelement=createFile(newfilename, filetype)
allsuspects[i].parentNode.replaceChild(newelement, allsuspects[i])
}
}
}[/COLOR]

P.S.
Is there a way to build some server side script that will generate a javascript file with an array of all avail Galleries based on the actual folders on the server.

---

