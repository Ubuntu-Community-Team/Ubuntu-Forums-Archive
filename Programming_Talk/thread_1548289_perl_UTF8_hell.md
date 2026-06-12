---
title: "perl UTF8 hell"
date: 2010-08-08
forum: Programming Talk
---

### Post by ian dobson on 2010-08-08
Hi All,

OK I've been banging my head on this one for afew days now and am not getting any further, so here goes:-

I've written a xmltv grabber (for my MythTV system) that grabs the TV program data from a network based tuner. The actual code works quite well (grabs the data, decodes it and writes out to a xmltv file that mythtv can read). The problem I'm having is that some characters (üèöéäà) are totally screwed up). To grab the webpage from the tuner I'm using the perl use LWP::Simple; module along the line of:-
```

    my $page = get($URL);
then decoding it using
        my $tcp = new HTML::TableContentParser;                         #And decode it
    return $tcp->parse($page);

```

And this is the webpage I'm trying to grab:-
```

<html>
	<head>
		<title>Service Electronic Program Guide (EPG)</title>
		<link rel="stylesheet" type="text/css" href="/webif.css">
		<script language="javascript" type="text/javascript" src="/window.js"></script>
		<script language="javascript" type="text/javascript" src="/epg.js"></script>
	</head>
	<body>
		<table id="epg" width="100%" border="0" cellspacing="0" cellpadding="5">
			<thead>
				<tr>
					<th colspan="3">RTL2</th>
				</tr>
			</thead>
			<tbody>
				<tr valign="middle">
	<td><span class="time">08.08.2010 08:25</span></td>
	<td>
		<a href="javascript:record('1:0:1:76e6:25b:1:0:0:0:0:','1281248700','7500','U-Boot in Not','RTL2')">
			<img src="timer.gif" border="0">
		</a>
	</td>
	<td class="genre01"> 
		<span class="event">U-Boot in Not</span>
		<br>Genre: Film<br>
		<span class="description">Nach einer Kollision sinkt das Atom-U-Boot 'Neptun' in bedrohliche Tiefen und bleibt am Rande eines Unterwasser-Canyons manövrierunfähig liegen. Nachdem es zunächst aussieht, als sei eine Bergung des Schiffes und seiner Mannschaft ohne nennenswerte Probleme möglich, erschüttern plötzlich heftige Seebeben die Region - die 'Neptun' wird unter Tonnen von Sand und Schlamm begraben...</span>
	</td>
</tr>

```

Note there is no HTML "header" definition for the character set. I have another script that uses LWP::Simple to grab a webpage from an extenal server ([http://www.scifi.de/tv-guide/?year=2010&&month=7&&day=28](http://www.scifi.de/tv-guide/?year=2010&&month=7&&day=28)) and the script appears to work. 

So is there a way to force LWP::Simple / HTML parse to use UTF8?

Regards
Ian Dobson

---

### Post by ian dobson on 2010-08-08
Hi,

OK I think I've got it. I added a "fake" meta header to the html before decoding it. Not nice but hay if it works.

Regards
Ian Dobson

---

### Post by gmargo on 2010-08-08
You can call the **utf8_mode()** method with a true argument (available from the **HTML::Parser** module that is the basis for **HTML::TableContentParser**.)

---

