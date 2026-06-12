---
title: "Convert an RSS link to Text format (with right chars)"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by honeybear on 2011-10-04
Hi,

I would like to convert an RSS file to a readable simple text file. How could it be possible. The problem is that I get images in it and links. How to remove this ?

[http://rss.lemonde.fr/c/205/f/3050/index.rss](http://rss.lemonde.fr/c/205/f/3050/index.rss)

Thank you !

---

### Post by cavh on 2011-10-04
In a terminal:

```
cd ~/Desktop; wget http://rss.lemonde.fr/c/205/f/3050/index.rss; gedit ~/Desktop/index.rss
```

---

### Post by honeybear on 2011-10-04
> **cavh said:**
> In a terminal:

```
cd ~/Desktop; wget http://rss.lemonde.fr/c/205/f/3050/index.rss; gedit ~/Desktop/index.rss
```


thanks but - well, for me it is kind of difficult to read ... 
```

<?xml version='1.0' encoding='UTF-8'?><?xml-stylesheet type='text/xsl' href='http://rss.lemonde.fr/xsl/fr/rss.xsl'?>
<rss xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:taxo="http://purl.org/rss/1.0/modules/taxonomy/" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" version="2.0"><channel><title>Le Monde.fr : à la Une</title><link>http://www.lemonde.fr</link><description>Toute l'actualité au moment de la connexion</description><language>en</language><copyright>Copyright Le Monde.fr</copyright><pubDate>Tue, 04 Oct 2011 19:27:54 GMT</pubDate><lastBuildDate>Tue, 04 Oct 2011 19:27:54 GMT</lastBuildDate><ttl>15</ttl><image><title /><url>http://medias.lemonde.fr/mmpub/img/lgo/lemondefr_rss.gif</url><link>http://www.lemonde.fr</link></image><item><title>Apple dévoile son iPhone 4S</title><link>http://www.lemonde.fr/technologies/article/2011/10/04/apple-devoile-son-iphone-4s_1582256_651865.html#ens_id=1581777&amp;#38;xtor=RSS-3208</link><description>Le groupe informatique a présenté une version améliorée de l'iPhone 4, sans véritables surprises. Il s'agit de la cinquième version du smartphone, depuis son lancement en 2007.&lt;img width='1' height='1' src='http://rss.lemonde.fr/c/205/f/3050/s/190a8df5/mf.gif' border='0'/&gt;&lt;br/&gt;&lt;br/&gt;&lt;a href="http://da.feedsportal.com/r/114252820378/u/0/f/3050/c/205/s/190a8df5/kg/260/a2.htm"&gt;&lt;img src="http://da.feedsportal.com/r/114252820378/u/0/f/3050/c/205/s/190a8df5/kg/260/a2.img" border="0"/&gt;&lt;/a&gt;</description><enclosure url="http://s2.lemde.fr/image/2011/10/04/87x0/1582273_7_cc45_philip-schiller-vice-president-en-charge-du.jpg" length="1895" type="image/jpeg" /><pubDate>Tue, 04 Oct 2011 19:01:08 GMT</pubDate><guid isPermaLink="false">http://www.lemonde.fr/technologies/article/2011/10/04/apple-devoile-son-iphone-4s_1582256_651865.html#ens_id=1581777&amp;#38;xtor=RSS-3208</guid></item><item><title>Montebourg : "Je n'ai pas de raison de penser que je pourrais échouer"</title><link>http://www.lemonde.fr/primaire-parti-socialiste/article/2011/10/04/montebourg-je-n-ai-pas-de-raison-de-penser-que-je-pourrais-echouer_1582264_1471072.html#ens_id=1402952&amp;#38;xtor=RSS-3208</link><description>Arnaud Montebourg était l'invité, mardi, du chat vidéo du "Monde" et de DailyMotion pour la primaire PS. Il promet notamment un gouvernement "étincelant" s'il parvient à l'Elysée.&lt;img width='1' height='1' src='http://rss.lemonde.fr/c/205/f/3050/s/190a8df6/mf.gif' border='0'/&gt;&lt;br/&gt;&lt;br/&gt;&lt;a href="http://da.feedsportal.com/r/114252820377/u/0/f/3050/c/205/s/190a8df6/a2.htm"&gt;&lt;img src="http://da.feedsportal.com/r/114252820377/u/0/f/3050/c/205/s/190a8df6/a2.img" border="0"/&gt;&lt;/a&gt;</description><enclosure url="http://s1.lemde.fr/image/2011/10/04/87x0/1582275_7_cc9f_arnaud-montebourg-etait-l-invite-mardi-du.jpg" length="2372" type="image/jpeg" /><pubDate>Tue, 04 Oct 2011 18:40:43 GMT</pubDate><guid isPermaLink="false">http://www.lemonde.fr/primaire-parti-socialiste/article/2011/10/04/montebourg-je-n-ai-pas-de-raison-de-penser-que-je-pourrais-echouer_1582264_1471072.html#ens_id=1402952&amp;#38;xtor=RSS-3208</guid></item><item><title>Montebourg : "Je n'ai pas de raison de penser que je pourrais échouer"</title><link>http://www.lemonde.fr/politique/article/2011/10/04/montebourg-je-n-ai-pas-de-raison-de-penser-que-je-pourrais-echouer_1582264_823448.html#ens_id=1402952&amp;#38;xtor=RSS-3208</link><description>Arnaud Montebourg était l'invité, mardi, du chat vidéo du "Monde" et de DailyMotion pour la primaire PS. Il promet notamment un gouvernement "étincelant" s'il parvient à l'Elysée.&lt;img width='1' height='1' src='http://rss.lemonde.fr/c/205/f/3050/s/190a7b51/mf.gif' border='0'/&gt;&lt;br/&gt;&lt;br/&gt;&lt;a href="http://da.feedsportal.com/r/114252696744/u/0/f/3050/c/205/s/190a7b51/a2.htm"&gt;&lt;img src="http://da.feedsportal.com/r/114252696744/u/0/f/3050/c/205/s/190a7b51/a2.img" border="0"/&gt;&lt;/a&gt;</description><enclosure url="http://s1.lemde.fr/image/2010/10/03/87x0/1419668_7_1b7c_arnaud-montebourg-le-22-aout-2010-a.jpg" length="1881" type="image/jpeg" /><pubDate>Tue, 04 Oct 2011 18:40:43 GMT</pubDate><guid isPermaLink="false">http://www.lemonde.fr/politique/article/2011/10/04/montebourg-je-n-ai-pas-de-raison-de-penser-que-je-pourrais-echouer_1582264_823448.html#ens_id=1402952&amp;#38;xtor=RSS-3208</guid></item><item><title>Les troubles psychosociaux liés au travail en hausse depuis dix ans</title><link>http://www.lemonde.fr/societe/article/2011/10/04/les-troubles-psychosociaux-lies-au-travail-en-hausse-depuis-dix-ans_1582263_3224.html#xtor=RSS-3208</l
```

---

### Post by cavh on 2011-10-04
Then simply open ~/Desktop/index.rss in the XML editor of your choice.

[http://ubuntuforums.org/showthread.php?t=552045&highlight=xml+editor]("http://ubuntuforums.org/showthread.php?t=552045&highlight=xml+editor")

---

### Post by honeybear on 2011-10-04
> **cavh said:**
> Then simply open ~/Desktop/index.rss in the XML editor of your choice.

[http://ubuntuforums.org/showthread.php?t=552045&highlight=xml+editor]("http://ubuntuforums.org/showthread.php?t=552045&highlight=xml+editor")

I would like to convert it to text format. 

So which would mean to convert this xml code to a something readable (using basH/sh or perl) to avoid firefox xml reading... 

purely text ;) would help a lot

---

