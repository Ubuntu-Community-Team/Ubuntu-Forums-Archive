---
title: "How to record streaming net radio"
date: 2007-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by phossal on 2007-01-10
The script below enables easy recording of an internet stream. Copy and paste the following into a file called: rec Make it executable, and then use sudo to move it to /usr/bin.

```
#!/bin/bash
#
# script to record MP3 broadcast stream
# The command is all on one line ending with a semi-colon
#
# $1 is the station
# $2 is the name of the music
#
#Replace <user> with your user name

/usr/bin/mplayer $1 -dumpstream -dumpfile /home/<user>/${2}.mp3 -vc dummy -vo null ;
```
The command works like this: rec [http://XX.XXX.X.XXX](http://XX.XXX.X.XXX) jazz, where [http://xx](http://xx).. is the IP of the station you want to record. The file will be saved as /home/<user>/jazz.mp3

---

### Post by marios88 on 2007-01-27
Just an excellent tutorial!!!! Many thanks! :D 


I was trying for days with many programs to rip Athens Red FM so i can listen while driving!!


:guitar: :guitar: :guitar:

---

### Post by phossal on 2007-01-27
> **marios88 said:**
> Just an excellent tutorial!!!! Many thanks! :D

All right! Rock on! I'm glad it helped you out, and I appreciate you taking the time to say thanks! Cheers!

---

### Post by indylarry on 2007-01-31
This is a great script.  I think I am going to try and use cron to run it so I can load my ipod for  work in the morning.

---

### Post by phossal on 2007-01-31
I dig that idea! My favorite *offline* radio stations make their content available online. I rip it and listen on my ipod, too.

---

### Post by jake3988 on 2007-02-01
There's no way to listen to it with mplayer as well?  Ie, you can only record it (with mplayer)?

Edit:  Doesn't work.  No mp3 is being created at all.  It does say its connected and displays the artist/song but nothing else happens.

Edit:  Oops, I'm terribly sorry.  It DOES work.  I decided to not use a pointless text file (no offense) but I kept using the playlist tag and it messed up the workings of mplayer.  I took away the playtest tag, and viola, it works!

---

### Post by phossal on 2007-02-01
> **jake3988 said:**
> 
Edit:  Doesn't work.  No mp3 is being created at all.  It does say its connected and displays the artist/song but nothing else happens.

Edit:  Oops, I'm terribly sorry.  It DOES work. ** I decided to not use a [COLOR="Red"]pointless text file (no offense)[/COLOR] but I kept using the playlist tag and it messed up the workings of mplayer**.  I took away the playtest tag, and viola, it works!

You're kidding, right?

I'm happy you were able to get yourself up and running. There are plenty of reasons which inspired me to use the text files. For a beginner, they're *both* valuable. They make the *options* seem *obvious*, rather than leading one to believe the command needs to be over complicated and maintained as one piece. Your own experience convinces me I'm correct. Do it the *easy* way first, so you *understand* it, and then do it your *own* way. As is the case in *all* of my tutorials, I set up my *own* system much differently than I suggest *others* do. Why? Because I'm not the one reading a *tutorial!* 

I appreciate that you were willing to admit *you* made a mistake. I only wish you had been more bashful in posting here (no offense), because I think it detracts from the thread. I would appreciate it if you would revise your post to say: "Please Remove", so I can have a mod delete it, or change its content entirely (perhaps to: thank you, or to: Thank you. It's also possible without the text file, like so and so...).

---

### Post by jake3988 on 2007-02-01
My god.  Get off your pride of a horse.

I realized by myself I made a mistake, figured out my own error, and ended up making a useless post.  Sue me.

And I was coming back here to edit in the file thanking you for the post.  But I sure as heck ain't going to do it now.

---

### Post by phossal on 2007-02-02
> **jake3988 said:**
> My god.  Get off your pride of a horse. I realized by myself I made a mistake, figured out my own error, and ended up making a useless post.  Sue me. And *I was coming back here to edit in the file thanking you for the post.  But I sure as heck ain't going to do it now.*

lol Wow. Follow up a useless, selfish post - one in which you simultaneously mount your own large (but dopey) horse by commenting on how you found the text file pointless and that the command doesn't work - with an insulting one. 

Again, I'm glad you're up and running. **I'm glad I could help *you* out.** Perhaps, in the future, you'll be able to contribute something to the forums (rather than *taking*), and experience someone like yourself. You might find reactions inspired less by pride, and more by *disappointment and irritation*. Once you've spent a few *hours*  helping out your fellow users and getting ungrateful-know-it-all-but-wrong responses in return, you'll consider it a thank you if those who take advantage of your efforts simply stay quiet.

Cheers. Happy Recording.

---

### Post by mcduck on 2007-02-03
Nice guide. But wouldn't it be easier to just use streamripper to do this? ;) It does all that easily from CLI, and integrates nice with Streamtuner.

---

### Post by phossal on 2007-02-03
Removed

---

### Post by mcduck on 2007-02-03
> **phossal said:**
> Heck ya! It *would* be easier, unless you never downloaded Streamtuner *or* Streamripper. Why not *explain* why it's valuable to do either, and then include a short how-to on, well, how-to. I don't, but a lot of people would *prefer* your way. I do like it when those who are more knowledgeable share their ideas though. Please do so (in a beginner-friendly way).

[Edit] I'm not sure if you want the *subjective* or *objective* answer to your main question. Subjective: *No.* Objective: *No.*
OK, here you go:

To install: 'sudo apt-get install streamripper'

To use: 'streamripper <URL>', replace <URL> with url to your stream. This will rip the stream into  current directory, separating each song to own file and naming the files if information is available.

Running 'streamripper -r <URL> creates a local relay on localhost:8000. You can then use that on your music player so you don't need to have 2 connections to the web radio to listen & rip at the same time.

You can use 'streamripper -a <URL>' to rip into a single file, and '-d' allows selecting directory for more options. 'man streamripper' will tell more.

For a GUI way, 'sudo apt-get install streamtuner' It will appear in your menus, and allows you to browse large selection of web radio streams and just hit record button to record the stream with streamripper.

---

### Post by phossal on 2007-02-03
Removed

---

### Post by guliver on 2007-02-04
I was following this tutorial and this is the error that I got:

> user@UBUNTU:~/Desktop$ record.sh
bash: record.sh: command not found


I use Ubuntu 6.10

Yes, I did all tutorial again and double checked and I did not miss any step...


Also when it record file how can I stop it and where does it save the file?

---

### Post by guliver on 2007-02-04
Also that GNOME recorder does not record :(

It output empty file......

ALso sometimes it doing strange things, if I select MIX as input it sqitch back to Capture by itslef as soon as I start recording :(

---

### Post by tpg on 2007-02-04
To run an executable in the directory you are currently in, you must prefix it with "./", i.e.
```
user@UBUNTU:~/Desktop$ ./record.sh
```

---

### Post by phossal on 2007-02-04
Removed

---

### Post by phossal on 2007-02-04
> **guliver said:**
> Also that GNOME recorder does not record :(
What is *GNOME recorder*?

---

### Post by Shay Stephens on 2007-02-04
> **phossal said:**
> What is *GNOME recorder*?

Probably refering to the gnome sound recorder "applications - sound & video - sound recorder"
```

gnome-sound-recorder

```

---

### Post by ice60 on 2007-02-04
it's pretty cool, i'll try it out thanks.

i do use streamtuner/streamripper though, but i'd still like to try this out.

i'm not sure if it was said, but the way i record with streamripper is by clicking on the record button in streamtuner when there's something i want to record.
1, launch streamtuner
2, double-click on a station to launch the media player and start listening
3, click on the record button in streamtuner to record.

 it makes directories for each radio station i think always in your home directory, then makes a separate mp3 for each tune 8)

---

### Post by ice60 on 2007-02-04
it's pretty cool, i'll try it out thanks.

i do use streamtuner/streamripper though, but i'd still like to try this out.

i'm not sure if it was said, but the way i record with streamripper is by clicking on the record button in streamtuner when there's something i want to record. [color=blue]edit[/color] it was said. well here's the gui way for all us lazy people lol
1, launch streamtuner
2, double-click on a station to launch the media player and start listening
3, click on the record button in streamtuner to record.

 it makes directories for each radio station, then makes a separate mp3 for each tune 8)

---

### Post by xanous on 2007-02-12
hmm... I was following along fine but when I got to making the excutable this is what I got

user@Ubuntu-desktop:~$ chmod +x /record.sh
chmod: cannot access `/record.sh': No such file or directory

I did everything exactly as the guide said to do. Even started over a couple of times from root and still came to the same result. 

Any ideas?

---

### Post by phossal on 2007-02-12
Removed

---

### Post by xanous on 2007-02-12
Oh sorry that is what I meant to say. I actually used many various forms of the same thing. 

but user@Ubuntu-desktop:~$ chmod +x record.sh is what I tried first.

 I am bit of a noob when it comes to linux and I just cant seem to find the problem. I got streamripper to work though but I would like to figure out your way as well. I will learn more that way.

I do have a streamripper question as well. How do I set it to stop recording at a certain time. I used -l and set it to 10 seconds but it is still running.  here is what I am looking at now.

user@ubuntu-desktop:~$ streamripper [http://ksco.got.net:9000](http://ksco.got.net:9000) -a [%t] - l 10
Connecting...
stream: KSCO AM 1080 Santa Cruz CA USA (831) 475-1080
server name: SHOUTcast/posix v1.8.0
bitrate: 32
meta interval: 8192

[ripping...    ]  -  [  1.27M]

it never stops.

---

### Post by xanous on 2007-02-12
Ah I see now. I tried it without the -a tag and it worked. I guess a better question is how to run more than one tag.

---

### Post by phossal on 2007-02-12
Removed

---

### Post by Gen2ly on 2007-02-14
I like the tutorial. Thanks.

Oh, and Ice60, if thats really a snapshot of you, could i but you a coffee latte?

---

