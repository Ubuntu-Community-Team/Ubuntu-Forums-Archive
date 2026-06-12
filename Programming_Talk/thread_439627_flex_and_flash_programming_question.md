---
title: "flex and flash programming question"
date: 2007-05-10
forum: Programming Talk
---

### Post by ubiwankanubi on 2007-05-10
I've just begun to learn about flex, so I can add flash to my website. While trying what should be a simple endeavor is turning out to take a long time to do. I'm trying to add a flash based mp3 player to my website. eventually I want to pass which song it plays via php variable (song.php?value=songname) or cookie. and perhaps even volume control.


here's what I've got cooking in flex now:
<?xml version="1.0" encoding="utf-8"?>
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml">
<mx:Sound id="bgm" source="01.mp3"/>
<mx:Panel id="panel" width="450" height="64">
<mx:Button label="Play" click="bgm.play()"/>
<mx:Button label="Pause" click="bgm.pause()"/>
<mx:Button label="Stop" click="bgm.stop()"/>
</mx:Panel>
</mx:Application>

the error i get is:
Error: Could not resolve <mx:Sound> to a component implementation.
<mx:Sound id="bgm" source="01.mp3"/>

so I'm sure I'm not using the Sound function correctly, but I don't know what should go there!

---

