---
title: "Playing Audio with pipeline in Gstreamer (C#)"
date: 2013-04-23
forum: Programming Talk
---

### Post by Apidcloud on 2013-04-23
[COLOR=#000000][FONT=Arial]I've been struggling with GStreamer for a while because I can't find any C# examples/tutorials.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]As far as I know, Gstreamer uses pipelines in order to decode and then be able to send, for instance a song, to the speakers, but I tried the following, which didn't work:
```

[COLOR=#2B91AF][FONT=Consolas]Gst[/FONT][/COLOR][FONT=Consolas].[/FONT][COLOR=#2B91AF][FONT=Consolas]Element[/FONT][/COLOR][FONT=Consolas] pipeline[/FONT][FONT=Consolas];
[/FONT][COLOR=#00008B][FONT=Consolas]string[/FONT][/COLOR][FONT=Consolas] path [/FONT][FONT=Consolas]=[/FONT][COLOR=#800000][FONT=Consolas]@"some_path.mp3"[/FONT][/COLOR][FONT=Consolas];
[/FONT][COLOR=#00008B][FONT=Consolas]string[/FONT][/COLOR][FONT=Consolas] command [/FONT][FONT=Consolas]=[/FONT][COLOR=#800000][FONT=Consolas]"filesrc location="[/FONT][/COLOR][FONT=Consolas]+[/FONT][FONT=Consolas] path [/FONT][FONT=Consolas]+[/FONT][COLOR=#800000][FONT=Consolas]" ! oggdemux ! vorbisdec ! audioconvert ! gconfaudiosink"[/FONT][/COLOR][FONT=Consolas];
[/FONT][FONT=Consolas]pipeline [/FONT][FONT=Consolas]=[/FONT][COLOR=#2B91AF][FONT=Consolas]Gst[/FONT][/COLOR][FONT=Consolas].[/FONT][COLOR=#2B91AF][FONT=Consolas]Parse[/FONT][/COLOR][FONT=Consolas].[/FONT][COLOR=#2B91AF][FONT=Consolas]Launch[/FONT][/COLOR][FONT=Consolas]([/FONT][FONT=Consolas]command[/FONT][FONT=Consolas]); 
[/FONT][FONT=Consolas]pipeline[/FONT][FONT=Consolas].[/FONT][COLOR=#2B91AF][FONT=Consolas]SetState[/FONT][/COLOR][FONT=Consolas]([/FONT][COLOR=#2B91AF][FONT=Consolas]Gst[/FONT][/COLOR][FONT=Consolas].[/FONT][COLOR=#2B91AF][FONT=Consolas]State[/FONT][/COLOR][FONT=Consolas].[/FONT][COLOR=#2B91AF][FONT=Consolas]Playing[/FONT][/COLOR][FONT=Consolas]);
[/FONT]
```
However, it raises an exception in the Gst.Parse.Launch line[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Does anyone know any good application example, and/or can actually post some code, so I can start getting used to the library? Also, if you can tell me what's wrong on the code above, I'd be thankful[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Without further ado, Regards[/FONT][/COLOR]

---

