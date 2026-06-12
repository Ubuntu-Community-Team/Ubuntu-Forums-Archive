---
title: "Open Source Alternative for this Asp.net http live upload?"
date: 2009-07-31
forum: Programming Talk
---

### Post by dolomite792 on 2009-07-31
I'm trying to get a webpage that shows all of the views of my cams at once hosted on one server so that i can securely view it.

I don't know Asp.net at all I'm a total newb at anything scripting and its been bothering me for a while.  I'm wondering if there is an open source solution instead of this microsoft crap so that i can view live motion jpg remotely?  The problem with that script there is that it only allows you one cam view at a time where as I wanted all 6 to display on the page but I am unsure as how to write it up.  Hopefully there is an easier way?  The cams won't port forward so its out of the question, this is my last hope.  Ive contacted every other party i can think of with no help from them this is one of my last hopes.

[http://www.axis.com/techsup/cam_servers/tech_notes/live_video_iis_httpupload.htm](http://www.axis.com/techsup/cam_servers/tech_notes/live_video_iis_httpupload.htm)

Here's what it says on the webpage:
-----------------------------------------------------------------
Preparing the Web server

   1.

      Create a virtual directory, for example named 'live' on your IIS server pointing to a folder, for example c:\inetpub\wwwroot\live on the server's hard disk.
   2.

      Download and unpack the necessary files IISupdate.zip (includes Global.asa, filesize.asp, http_upload.asp, readImage.asp, view.htm) in the above folder.
   3.

      Configure an Axis network video product to perform HTTP upload of images to the http_upload.asp file i.e. in this case the necessary URL in the Event Server configuration would be:

      [http://[Web_server]/live/http_upload.asp](http://[Web_server]/live/http_upload.asp)

      In the Event Type configuration configure HTTP upload to the above server with the desired image frequency (for example 1 frame per second). Use Overwrite option.
   4.

      View a still image through the readImage.asp script, for example:

      [http://[Web_server]/live/readImage.asp](http://[Web_server]/live/readImage.asp)
   5.

      View JavaScript updated video from the view.htm file, for example:

      [http://[Web_server]/live/view.htm](http://[Web_server]/live/view.htm)

      The implementation is done in the following way:

      In the Global.asa file a global variable is defined that will contain the entire image file.

      The http_upload script will insert the image file into this global variable and update it when a new image is sent from the camera. The readImage will simply get the global variable and send it to the user. 


-----------------------------------------------------------------

Ok well here is what each file from the link says:

Filesize.asp:



> 
<html>
<body>

	

<%  dim a
   ' a = 0
    a = Application("CurrentImage") 
%>

<%= a %>

</body>
</html>



The next is Global.asa:

> <SCRIPT LANGUAGE=VBScript RUNAT=Server>
Option Explicit

 Dim imageSize
 Dim  theImage 

imageSize = 0
theImage = ""

Sub Application_OnStart() 
   Application("imageSize") = imageSize
   Application("theImage") = theImage

End Sub   

</SCRIPT>

And the Next is http_upload.asp

> <%


biData = Request.BinaryRead(Request.TotalBytes)

if len(bidata) > 0 then 
   
  Application("imageSize") = LenB(biData)	
  Application("theImage") = biData	
    	
end if

%>
<html>
<body>
File uploaded successfully!
</body>
</html>



and the next is readimage.asp

> <%
Response.Buffer  = True
Response.Clear
Response.Expires = 0

Response.AddHeader"Cache-Control","no-cache"
Response.AddHeader"Pragma","no-cache"

Response.contenttype = "image/jpeg"

Dim b 
b =   Application("theImage")
Response.binarywrite b
Response.End

%>



and the next is view.htm:

> <HTML>
<HEAD>
<TITLE>Demo of java refresh</TITLE>
</HEAD>

<CENTER>


<SCRIPT LANGUAGE="JavaScript">

var ImageReloaded = 0;

var BaseURL = "/";
// This is the path to the image generating asp file.
var File = "live/readImage.asp";

// Force an immediate image load
var theTimer = setTimeout('reloadImage()', 1);

// This function will stop unneeded reloads if client has slow bandwidth
function ImageLoaded() 
{
  ImageReloaded = 1;
}


function reloadImage()
{
  // Reload the image every one second (1000 ms)
  theTimer = setTimeout('reloadImage()', 1000);

  // Here we load the image
  if (ImageReloaded=1)
   {   
     theDate = new Date();
     var url = BaseURL;
     url += File;
     url += '?dummy=' + theDate.getTime().toString(10);
     // The dummy above enforces a bypass of the browser image cache

     document.theImage.src = url;
     ImageReloaded = 0;
   }   
}

document.write('<img name="theImage" onload="ImageLoaded()" src="" height="480" ');
document.write('width="640" alt="Live image">');
</SCRIPT>


</CENTER>


</HTML>




---

