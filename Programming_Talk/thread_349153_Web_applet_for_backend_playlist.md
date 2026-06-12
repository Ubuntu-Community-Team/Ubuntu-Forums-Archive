---
title: "Web applet for backend playlist"
date: 2007-01-29
forum: Programming Talk
---

### Post by xOrphenochx on 2007-01-29
I said I'd help someone with their convention, I'm doing the video rooms and he came up with a nice idea for scheduling. Apparently the first person before me had a list of files and times that they were to be played, just a simple text document, and when there was free time it would play commercials. 

On to the main point, the person who is running it asked me if I could make a web applet to help schedule the shows. It needs to read the file for the names and times already allotted and make a list on an html page and provided a combo box with other times to set and if something was changed write to that playlist file.

It sounds like I'm not really helping him, but I'm actually fixing all of the playback problems and not the actual way it "works", I have yet to actually go out to his house since we're about 2 hours away and always busy. 

If anyone has any suggestion as to what I can use or how to accomplish it, that would be much appreciated.

---

### Post by yaaarrrgg on 2007-01-30
Not sure you need an applet (as in java), but just a form on a web page that reads and writes out an xml file to disk.  What language you use (for example php) will depend on what server you are running.  Any language suitable for server side web scripting would work .  

Real player and win media player use an xml file for scheduling shows (IIRC) ... so you need to know the format you will be writting as.  To edit, you'd do the reverse: you'd parse the xml, and prefill your web form.  For this direction, might also help to glance at XSLT transforms... or some XML parser.

Assuming all the media is on the server, this should be all you need.  Otherwise, you'll also need some way of uploading the actual media...

---

