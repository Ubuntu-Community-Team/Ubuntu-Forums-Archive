---
title: "Help needed for script to scrape TV data from thetvdb.com for MythTV"
date: 2007-10-25
forum: Programming Talk
---

### Post by dfreer on 2007-10-25
Hi everyone,

   I'm in no way a master of scripting, being mostly self-taught trying to accomplish various tasks here and there. Right now, I'm trying to import all of my previously recorded TV shows to my MythTV database, using [http://thetvdb.com](http://thetvdb.com) to provide the data for each show. 

   I've run into two problems so far: I have an xml file containing about 4 paragraphs (depending on the show) that I have to parse for data, trimmed up. The other issue is that although I know how to get the first file, I don't know how to get the second file that contains the metadata information I need (more information in script).

Here's my script so far (I'm using bash. I'm more than willing to use perl, especially since mythtv uses perl anyways. I just happen to know bash better so that's what I started the script with). I trimmed up some comments so it's not quite as long:
```
#!/bin/bash
# Example usage:
# ./mythscrapetv.sh Supernatural\ -\ 101\ -\ Pilot.avi

video_filename="$1"

## Get the series name and episode number from filename.

series_name="`echo $video_filename | cut -d'-' -f1`"
season_number="`echo $video_filename | cut -d'-' -f2 | cut -d' ' -f2 | cut -c'1'`"
episode_number="`echo $video_filename | cut -d'-' -f2 | cut -d' ' -f2 | cut -c'2,3'`"

## For anyone interested, more information on thetvdb.com's interface:
## http://thetvdb.com/?tab=xml
wget http://thetvdb.com/interfaces/GetSeries.php?seriesname=$series_name -O ~/mythtemp

## Here's where I need some help:
## Since GetSeries will return several possible matches, I've got to 
## parse the file and get the series_id from the show I want
## Here's what the file will look like: 
## http://thetvdb.com/interfaces/GetSeries.php?seriesname=Supernatural

series_id="$results_from_parse"

## Somehow, I've gotta parse a xml file (I'm not sure on how to get it yet)
## To get the episode name, original airdate, length, network it airs on, 
## and a short description of the episode. All of this can be found for this
## particular example here: 
## http://thetvdb.com/?tab=episode&seriesid=78901&seasonid=15827&id=298554&lid=7

episode_title=""
episode_datetime=""
episode_length=""
network=""
episode_desc=""


##
# Rebuilding the database...
##
## This perl script asks several questions, which can be answered in 
## advance using the paramater --answer. So this should all work at the 
## end:

myth.rebuilddatabase.pl --norename --file $video_filename \
--answer y \
-- answer "$network" \
--answer "$series_name" \
--answer "$episode_title" \ 
--answer "$episode_desc" \
--answer "$episode_datetime" \
--answer "$episode_length" \
--answer y

```

Does anyone think they can help, or offer any improvements to this script? It will eventually do the following once I get it working with a single file:
[list]
[*]Run the script in a directory, and it will link any files with specific extensions to the recording directory, recursively scanning the folders below the current directory.
[*]Scrape all of the metadata for the shows, and then add them into the mythtv database correctly.
[*]The first time it encounters multiple choices for a series, ask which Series should be used, then store preference in file. Other than that, be totally autonomous, just point the script at the directory and leave.
[/list]

---

### Post by Solarbaby on 2007-11-04
Dfreer:

I was googling and I came across this masterpiece.. 

[http://svn.whuffy.com/index.fcgi/wiki](http://svn.whuffy.com/index.fcgi/wiki)

I was interested when I read about this..

> 

**Description / Features**
Shepherd knows enough about the capabilities of each grabber in order to make intelligent judgments about which is most appropriate for any given situation, maximizing data quality while minimizing bandwidth usage. It analyses the XML output from each grabber to determine whether any further grabbers are required to obtain a full dataset of the required channels. It then employs postprocessor components to further refine the data: the imdb_augment_data postprocessor adds movie information from IMDb.com, tvdb_augment_data adds series/episode details from [COLOR="deepskyblue"]TheTVDB.com[/COLOR], flag_aus_hdtv marks shows that are available in High Definition, and more.  


Maybe you can find what your looking for in there..  as always best luck to you!

---

### Post by dfreer on 2007-11-04
Thanks a lot for the link! It looks to be used with mythtv, I'll investigate to see whether this can be used when importing tv shows, thanks again!

---

### Post by Protoss on 2008-05-24
Any updates on this? I love the library feature of XBMC for Linux, but it's too unstable at the moment, and won't play some of my MKVs, while Myth plays them fine.

---

### Post by ingeon on 2010-01-16
> **Protoss said:**
> Any updates on this? I love the library feature of XBMC for Linux, but it's too unstable at the moment, and won't play some of my MKVs, while Myth plays them fine.

Yeah, mythtv is awesome but XBMC (my version also still slow&buggy) is very clever in terms of finding and downloading thetvdb.com & [www.imdb.com](www.imdb.com) and matching it.
I hope mythtv will have something similar and easy soon

I now want to put all my DVD boxsets on my HDD as Xvid and and once I am done i want to pull in all the info from thetvdb.com&[www.imdb.com](www.imdb.com). What is the best way to do this using mythvideo?

---

### Post by dfreer on 2010-01-16
> **ingeon said:**
> Yeah, mythtv is awesome but XBMC (my version also still slow&buggy) is very clever in terms of finding and downloading thetvdb.com & [www.imdb.com](www.imdb.com) and matching it.
I hope mythtv will have something similar and easy soon

I now want to put all my DVD boxsets on my HDD as Xvid and and once I am done i want to pull in all the info from thetvdb.com&[www.imdb.com](www.imdb.com). What is the best way to do this using mythvideo?

Probably best if you created a new thread with this question, as this one is quite dead.

---

