---
title: "Configure StreamTuner to use Amarok"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by LarryJ2 on 2008-11-27
Streamtuner version 0.99.99  is setup to use XMMS media player.  Unfortunately  XMMS is no longer available in the repository.  I prefer amarok audio media player anyway,  so this guide shows how to configure streamtuner to use amarok rather than xmms.

1.  Install streamtuner  and amarok using  synaptic.  Versions I used were streamtuner v0.99.99  and amarok 1.4.9.1 in Ubuntu 8.04

2.  Open streamtuner (Should be in Gnome  *Applications* -> *Sound and Video*)

3.  In streamtuner,  *Edit* -> *Preferences * click and highlight the line "Listen to a stream".

4. Carefully position your mouse cursor over the right column of the line beginning with "Listen to a stream".

4.5 While in this position, issue  one   left click.

5. The  right hand half of the line which is headed "Command" should be flip to highlighted so that you can edit it.

6. Replace       ***xmms %q***      with       ***amarokapp -p %q***

7. Click *Close*.

8. Now test the configuration:    In streamtuner,  click *Stream* >*New Preselection*.  For example, using the National Public Radio Stream

Name:  **National Public Radio**
Genre:  **news**
Homepage: **[http://www.npr.org/stations/donate/index.php?ps=st2](http://www.npr.org/stations/donate/index.php?ps=st2)**
URL: [**http://stream.npr.org:8002/listen.pls**](**http://stream.npr.org:8002/listen.pls**)

Click *Apply*   then  click *OK*

9.  Then to listen to NPR by invoking the media player amarok.   In streamtuner,  high light the National Public line in *Preselections*.

10  Click the  Green triangle "Tune In".


That's it.  If I missed anything,  please add to this thread.  I've been into Linux for two years and I still stumbled over this simple task.  I'm sure many other beginners will also!

Also  many media players including amarok allow you to input the stream url directly with out using streamtuner.  For example, in amarok,
click *Playlists* -> *Add stream*.  In the Add Stream -Amarok text edit, you would enter  "http://stream.npr.org:8002/listen.pls" , again using NPR as an example.

This guide presupposes that you have sound coming from your speakers. Say you've followed these steps, you see a bouncing spectrum bar graph at the bottom of aramok's main window but you don't hear anything from your speakers. Try this: go into  *Syste*m -> *Preferences* -> *Sound*.  Click the Test buttons and see if you can get output from your speakers.  Good luck!

Larry

---

### Post by socref on 2008-11-27
> **LarryJ2 said:**
> Streamtuner version 0.99.99  is setup to use XMMS media player.  Unfortunately  XMMS is no longer available in the repository.  I prefer amarok audio media player anyway,  so this guide shows how to configure streamtuner to use amarok rather than xmms.

1.  Install streamtuner  and amarok using  synaptic.  Versions I used were streamtuner v0.99.99  and amarok 1.4.9.1 in Ubuntu 8.04

(some snipping)

10  Click the  Green triangle "Tune In".


(more snipping)

Larry

Larry, thanks! This was very useful. I just upgraded to 8.04 and was frustrated that XMMS was suddenly out of the picture.

One question for you... After making the changes you suggested I am having a terrible time getting ShoutCast to play. Is ShoutCast screwed up or does something else need to be done to get it to play through Streamtuner?

Thx
socref

---

### Post by LarryJ2 on 2008-11-28
> I am having a terrible time getting ShoutCast to play. Is ShoutCast screwed up 

I didn't try tuning ShoutCastfrom within streamtuner until this morning. When I did,  I didn't see a list of streams which I expected in the streamtuner gui.  Xiph,all , Google Stations, basic.ch,  punkcast.com  all dislayed stream selections. 

However,  Live365 and SHOUTcast refused to display anything.  No error messages were returned either.  I'm guessing that the plugins need updating?

Just for fun, I installed tunapie whose description says it tunes SHOUTcast streams.  It installed and ran but I couldn't tell if the streams displayed were from the SHOUTcast list or not.   Nice program, however,  I'll keep it around.

Also,  FYI Amarok appears to list and play the SHOUTcast streams.

---

