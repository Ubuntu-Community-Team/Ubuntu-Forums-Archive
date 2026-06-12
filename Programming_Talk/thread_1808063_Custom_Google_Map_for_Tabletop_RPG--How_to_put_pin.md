---
title: "Custom Google Map for Tabletop RPG--How to put pins in it?"
date: 2011-07-19
forum: Programming Talk
---

### Post by tarahmarie on 2011-07-19
Yes, I'm a nerd. Get over it.

Ok, so my gaming group has a site I built; WordPress over MediaWiki, etc etc for our stuff.

Here's something my GM really wants and so do I: a map that we can put custom tiles in, with pins, directions, etc. I know there's a way to overlay the Google Maps functionality on a custom map. I have already generated the tiles and used a Bing Maps tutorial out of MS Research (yes, yes, I know, but no one seems to know how to do this OSS-style), and you can see the map here:

[http://earthdawn.tarahwheeler.com/map/](http://earthdawn.tarahwheeler.com/map/)

Like you can see, I've made the tiles, you can zoom in, etc. Still, there's no way to add information to the map. What do I do--set up a MySQL db, hook it into the page, allow logged in people to edit and pin and add tiles, etc? How do I do this with Google Maps?

Here's the code that runs that page:

```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<head>

        <title>MapCruncher Mashup Sample Web Page</title>

        <script src="http://dev.virtualearth.net/mapcontrol/mapcontrol.ashx?v=5" type="text/javascript"></script>
        <script src="http://research.microsoft.com/mapcruncher/scripts/v5.5/CrunchControl.js" type="text/javascript"></script>
        <link href="http://research.microsoft.com/mapcruncher/scripts/v5.5/LegendStyle.css" rel="stylesheet" type="text/css">

        <script type="text/javascript">

        var div = null;
        var map = null;
        var crunchedLayerManager = null;

        function ToggleLayer(name, active)
        {
                if (active == true)
                {
                        crunchedLayerManager.layerList.find(name).Activate(map);
                }
                else
                {
                        crunchedLayerManager.layerList.find(name).Deactivate(map);
                }
        }

        function searchboxactivate()
        {
            txt = document.getElementById('searchbox').value;
            map.Find(txt, "");
        }        

        function GetSize()
        {
                var myWidth = 0, myHeight = 0;

                if( typeof( window.innerWidth ) == 'number' ) {
                    //Non-IE
                    myWidth = window.innerWidth;
                    myHeight = window.innerHeight;
                } else if( document.documentElement && ( document.documentElement.clientWidth || document.documentElement.clientHeight ) ) {
                    //IE 6+ in 'standards compliant mode'
                    myWidth = document.documentElement.clientWidth;
                    myHeight = document.documentElement.clientHeight;
                } else if( document.body && ( document.body.clientWidth || document.body.clientHeight ) ) {
                    //IE 4 compatible
                    myWidth = document.body.clientWidth;
                    myHeight = document.body.clientHeight;
                }

                if (myWidth > 0)
                {
                        var result = new Array();
                        result[0] = myWidth;
                        result[1] = myHeight;
                        return result;
                }
                else
                {
                        return null;
                }
        }

        function SetMapSize()
        {
                var browserSize = GetSize();

                var div = document.getElementById("Map");

                if (browserSize != null)
                {
                        div.style.width = (browserSize[0] - 25) + "px";
                        div.style.height = (browserSize[1] - 25) + "px";

                }
                else
                {
                        div.style.width = "800px";
                        div.style.height = "600px";
                }
                div.style.overflow = "hidden";
                div.style.position = "relative";

				if (crunchedLayerManager!=null)
				{
					crunchedLayerManager.controlManager.UpdateControlLayout();
				}
        }

        function MapModeChanged(e)
        {
                if (map.GetMapMode() == Msn.VE.MapActionMode.Mode3D &&
                    window.location.protocol == "file:")
                {
                        alert("MapCruncher tiles will only display in 3D mode " +
                        "if your map is hosted on a web server (using http://).\n" +
                        "Currently, your tiles are coming from a local machine (file://) " +
                        "so only 2D mode is available.");
                }
        }

        function LoadPage()
        {
                SetMapSize();
                window.onresize = SetMapSize;

                map = new VEMap('Map');
                map.LoadMap();
                map.AttachEvent("oninitmode", MapModeChanged);
                map.SetMapStyle('h');

				crunchedLayerManager = new VE.MapCruncher.CrunchedLayerManager(map);
				crunchedLayerManager.controlManager.AddControl(
						"aboutDiv", "",
						new VE.MapCruncher.LayoutSpec("right", 10, "top", 12),
						true, false);
                crunchedLayerManager.ImportLayersFromAnchorHRef("CrunchedLayers");
                var permalinkProvided = crunchedLayerManager.ApplyPermalink(document.layerCheckboxForm);

                if (!permalinkProvided) {
          var layer = crunchedLayerManager.layerList.find('NewLayer');
                    layer.Activate(map);
                    layer.SetDefaultView(map);
                }
        }

        </script>

</head>
<body onload="LoadPage()">

<div id="Map"></div>

<div style="display:none">
	<a id="CrunchedLayers" href="MapCruncherMetadata.xml">CrunchedLayers</a>
</div>

<div id="aboutDiv" style="background:white; width:400px; border: 2px solid #0000c0">
<div style="padding:10px">
<p> Welcome to Earthdawn.
<p>


<form action="javascript:searchboxactivate()">
	<b>Search the map for locations:</b>
	<input id="searchbox" type="text" name="searchbox" size="20">
	<input id="sbutton" type="button" value="Go!" onclick="javascript:searchboxactivate()">
</form>
<!--
        <form action="None" name="layerCheckboxForm">        
<b>Select Mashup Layers:</b>
<input type="checkbox" id="checkbox:NewLayer" onClick="javascript:ToggleLayer('NewLayer', this.checked);" checked>NewLayer&nbsp;<a href="javascript:crunchedLayerManager.layerList.find('NewLayer').SetDefaultView(map);"><font size="-1">center here</font></a>&nbsp;|
</form>
-->
</div>
</div>

</body>
</html>



```

---

### Post by noelvh on 2011-07-21
Hi, it looks cool but I want to share a tool (free tool) you might like. RPtools.net. Not sure if it will be what you are looking for, but I have used it and love it for map building small and large.
Noel

---

### Post by tarahmarie on 2011-07-21
I like it in a lot of ways, and it might be useful for smaller maps, but we want our map just like Google Maps; a huge canvas that we can individually improve and fiddle with.

How do I load Google Maps using HTML and a CUSTOM SET OF TILES?

---

### Post by tarahmarie on 2011-07-22
There has to be one human out there who has created a custom Google Map with their own tiles.

---

### Post by ve4cib on 2011-07-22
[Minecraft Overviewer](https://github.com/brownan/Minecraft-Overviewer/wiki) does pretty much exactly what you describe.  It creates a custom set of tiles (in this case based on a Minecraft world), and creates an HTML page that uses Google Maps to load and display the tiles.  [Here's an example.](http://overviewer.org/example/#/-288/64/137/-2/mcmapNormal)

You might be able to rip off some of that code (it's open-source, and on Github) to suit your purposes.

Once you have the map (either Google, Bing, or whatever) I would imagine you could use their Javascript APIs to add the appropriate pushpins.  I've used both in the past to create GIS web applications, and their APIs are pretty similar.  You specify a latitude & longitude you want to place a pushpin, and *poof* there it appears.

---

