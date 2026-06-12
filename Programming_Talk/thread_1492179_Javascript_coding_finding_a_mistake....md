---
title: "Javascript coding finding a mistake..."
date: 2010-05-24
forum: Programming Talk
---

### Post by emigrant on 2010-05-24
Im stuck in the midway of a program.
is there any one who would be willing to help?
thank you very much.

PS: the coding is in one file (html) so i can post the whole code here if anyone is out there to help.

---

### Post by Sub101 on 2010-05-24
Post the code. Preferably only the problem area. We cant help without it.

---

### Post by emigrant on 2010-05-24
> **Sub101 said:**
> Post the code. Preferably only the problem area. We cant help without it.

that was quick.
i will post the the file itself so you can run and see whats going on.

what i need to happen is,
once i click the 'drive me there' button,
an alert should pop out displaying the bus numbers.

i pass two values (places) to the print() and it should determine the right array of bus numbers corresponding to the location.
and after that the check() checks the matching bus numbers.

the problem is neither the print() nor check() seems to do the supposed work.
hope thats clear.

thanks.


[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"  xmlns:v="urn:schemas-microsoft-com:vml">
  <head>
    <meta http-equiv="content-type" content="text/html; charset=utf-8"/>
    <title>Map your route with InfoMap: Advanced Directions</title>
    <script src=" http://maps.google.com/?file=api&amp;v=2.x&amp;key=ABQIAAAAzr2EBOXUKnm_jVnk0OJI7xSosDVG8KKPE1-m51RBrvYughuyMxQ-i1QfUnH94QxWIa6N4U6MouMmBA"
      type="text/javascript"></script>
    <style type="text/css">
      body {
        font-family: Verdana, Arial, sans serif;
        font-size: 11px;
        margin: 2px;
      }
      table.directions th {
    background-color:#EEEEEE;
      }
      
      img {
        color: #000000;
      }
    </style>
    <script type="text/javascript">


     
 
    var map;
    var gdir;
    var geocoder = null;
    var addressMarker;
    var resultArray1=new Array();
    var str1Array=new Array("100");
    var str2Array=new Array("100");

    var loc1="Wellawatte Police Station, Sri Lanka";
    var loc2="Waidya Rd, Sri Lanka";
    var loc3="Havelock Town, Sri Lanka";
    var loc4="Slave Island, Sri Lanka";

//array consisting the bus numbers of locations
    var loc1Array=new Array("100", "101", "400", "430", "02");
    var loc2Array=new Array("100", "101");
    var loc3Array=new Array("400", "430", "02");
    var loc4Array=new Array("100", "101",  "02");


    function print(input1, input2){
    
    switch(input1){
    case "Wellawatte Police Station, Sri Lanka": str1Array=loc1Array;break;
    case "Waidya Rd, Sri Lanka": str1Array=loc2Array;break;
    case "Havelock Town, Sri Lanka": str1Array=loc3Array;break;
    case "Slave Island, Sri Lanka": str1Array=loc4Array;break;
    default: str1Array=loc2Array;
    }

switch(input2){
    case "Wellawatte Police Station, Sri Lanka": str2Array=loc1Array;break;
    case "Waidya Rd, Sri Lanka": str2Array=loc2Array;break;
    case "Havelock Town, Sri Lanka": str2Array=loc3Array;break;
    case "Slave Island, Sri Lanka": str2Array=loc4Array;break;
    default: str2Array=loc2Array;
    }
    
    //function starts here
    function check(str1Array, str2Array){
var a=0;

if(str1Array.length<str2Array.length)
    resultArray=new Array[str2Array.length];
else
    resultArray=new Array[str1Array.length];
var i=0;
for(i=0;i<str1Array.length;i++){
    var j=0;
    for(j=0;j<str2Array.length;j++){
    if(str1Array[i]==str2Array[j])
    {
        resultArray[a++]=str1Array[i];
    }
    }
} resultArray1=resultArray;
}
//function ends here
    
//to check whethe the alert works:
//alert("Please Take this Bus "+str1Array[0]+","+str1Array[1]+","+str1Array[2]);
alert("Please Take this Bus "+resultArray[0]+""+resultArray[1]);
}
    

    function initialize() {
      if (GBrowserIsCompatible()) {      


        map = new GMap2(document.getElementById("map_canvas"));




// ====== Restricting the range of Zoom Levels =====
      // Get the list of map types      
      var mt = map.getMapTypes();
      // Overwrite the getMinimumResolution() and getMaximumResolution() methods
      for (var i=0; i<mt.length; i++) {
        mt[i].getMinimumResolution = function() {return 7;}
        mt[i].getMaximumResolution = function() {return 18;}
      }
//=========ends here=======
    //map.addControl(new GSmallMapControl());
    map.addControl(new GLargeMapControl());
        gdir = new GDirections(map, document.getElementById("directions"));
        GEvent.addListener(gdir, "load", onGDirectionsLoad);
        GEvent.addListener(gdir, "error", handleErrors);


        setDirections("Dehiwala, Sri Lanka", "Bambalapitiya, Sri Lanka", "en_US");


      }
    }



     
    function setDirections(fromAddress, toAddress, locale) {
      gdir.load("from: " + fromAddress + " to: " + toAddress,
                { "locale": locale });
    }

    function handleErrors(){
       if (gdir.getStatus().code == G_GEO_UNKNOWN_ADDRESS)
         alert("No corresponding geographic location could be found for one of the specified addresses. This may be due to the fact that the address is relatively new, or it may be incorrect.\nError code: " + gdir.getStatus().code);
       else if (gdir.getStatus().code == G_GEO_SERVER_ERROR)
         alert("A geocoding or directions request could not be successfully processed, yet the exact reason for the failure is not known.\n Error code: " + gdir.getStatus().code);
       
       else if (gdir.getStatus().code == G_GEO_MISSING_QUERY)
         alert("The HTTP q parameter was either missing or had no value. For geocoder requests, this means that an empty address was specified as input. For directions requests, this means that no query was specified in the input.\n Error code: " + gdir.getStatus().code);

    //   else if (gdir.getStatus().code == G_UNAVAILABLE_ADDRESS)  <--- Doc bug... this is either not defined, or Doc is wrong
    //     alert("The geocode for the given address or the route for the given directions query cannot be returned due to legal or contractual reasons.\n Error code: " + gdir.getStatus().code);
         
       else if (gdir.getStatus().code == G_GEO_BAD_KEY)
         alert("The given key is either invalid or does not match the domain for which it was given. \n Error code: " + gdir.getStatus().code);

       else if (gdir.getStatus().code == G_GEO_BAD_REQUEST)
         alert("A directions request could not be successfully parsed.\n Error code: " + gdir.getStatus().code);
        
       else alert("An unknown error occurred.");
       
    }

    function onGDirectionsLoad(){ 
      // Use this function to access information about the latest load()
      // results.

      // e.g.
      // document.getElementById("getStatus").innerHTML = gdir.getStatus().code;
      // and yada yada yada...
    }


   
    </script>

  </head>
  <body onload="initialize() " onunload="GUnload()">
  



<DIV id=one ALIGN=CENTER>
  <h2>Welcome to InfoMap</h2>

<img src="http://img697.imageshack.us/img697/4521/48531661.jpg" border="0" />





  <form  action="#" onsubmit="setDirections(this.from.value, this.to.value, this.locale.value); print(this.from.value,this.to.value);return false;" >


  <table>
</DEV>




<tr><th>Source:&nbsp;</th>
   <td colspan="3"><select id="fromAddress" name="from">

    <option value="Wellawatte Police Station, Sri Lanka" selected>K's House</option>

    <option value="Waidya Rd, Sri Lanka">B's House</option>

    <option value="Havelock Town, Sri Lanka">Havelock Town</option>

    <option value="St Michaels Rd, Sri Lanka">ST</option>

    <option value="Kalubowlia, Sri Lanka">Hospital</option>

   <option value="Slave Island, Sri Lanka">A's House</option>

   <option value="Maradana, Sri Lanka">Maradana</option>

   <option value="Lotus Rd, Sri Lanka">Ministry of Planning</option>

   <option value="Cambridge Pl, Colombo">National Museum</option>

   <option value="Sri Lanka Rupavahini Corporation, Colombo, Sri Lanka">Rupavahini Corporation</option>
   
   <option value="American College of Higher Education, Dehiwala, Sri Lanka">Marlon's House</option>


   <option value="Dharmapala Rd, Colombo">Viharamahadevi Park</option>

    </select></td>

<tr><th>Destination:&nbsp;</th>
   <td colspan="3"><select id="toAddress" name="to">

    <option value="Wellawatte Police Station, Sri Lanka" selected>K's House</option>

    <option value="Dehiwala, Sri Lanka">B's House</option>

    <option value="Havelock Town, Sri Lanka">Havelock Town</option>

    <option value="St Michaels Rd, Sri Lanka">ST</option>

    <option value="Kalubowlia, Sri Lanka">Hospital</option>

   <option value="Slave Island, Sri Lanka">A's House</option>

   <option value="Maradana, Sri Lanka">Maradana</option>

   <option value="Lotus Rd, Sri Lanka">Ministry of Planning</option>

   <option value="Cambridge Pl, Colombo">National Museum</option>

   <option value="Sri Lanka Rupavahini Corporation, Colombo, Sri Lanka">Rupavahini Corporation</option>
   
    <option value="American College of Higher Education, Dehiwala, Sri Lanka">Marlon's House</option>

   <option value="Dharmapala Rd, Colombo">Viharamahadevi Park</option>

    </select></td>




   <tr><th>Language:&nbsp;</th>
   <td colspan="3"><select id="locale" name="locale">

    <option value="en" selected>English</option>

    <option value="fr">French</option>

    <option value="de">German</option>
    <option value="ja">Japanese</option>
    <option value="es">Spanish</option>
    </select>

    <input id="submit" type="submit" value="Hurry Up, Take Me There!"/><br>

<h1 id="myHeader" onclick="getValue()">Which Bus to Take...</h1>

   </td></tr>

   </table>

    
  </form>

    <br/>
    <table class="directions">
    <tr><th>Formatted Directions</th><th>Map</th></tr>

    <tr>
    <td valign="top"><div id="directions" style="width: 275px"></div></td>
    <td valign="top"><div id="map_canvas" style="width: 600px; height: 468px"></div></td>

    </tr>
    </table> 

<script type="text/JavaScript">




</script>



    </body>


</html>
[/HTML]

---

### Post by era86 on 2010-05-24
I don't have time to debug this all for you, but have you tried stepping through your code?  Which browser are you using to run it?  You might try setting a breakpoint in your code and step through it from there.

I'll try and take a closer look after work.  Goodluck.

---

