---
title: "How about an a2mp3 frontend?"
date: 2007-03-11
forum: Programming Talk
---

### Post by Takmadeus on 2007-03-11
Greetings and salutations!

I was looking around for the packages listed in synaptic and found a curious one....

[CENTER]*a2mp3 - program to optimize your music for your mp3 player*[/CENTER]

 [CENTER][I]a2mp3  is a program that Automates the task of optimizing your music to
       the needs of your mp3-player and keep the size at a  minimum.  It  con&#8208;
       verts  all  files given at commandline to your personal folder given in
       your configfile. The default folder is ~/mp3tmp.
[/I][/CENTER]

so I thought... hmmm it seems interesting, but it is kind of tiresome to write by hand all the filenames so I get my music optimized.... so.....

I am thinking of making a frontend to it in GAMBAS (GAMbas is not BASic) which is the only programming IDE that I almost know how to work with.... so I am going to try to remember all my Gambas knowledge (pretty small knowledge I might say) and make a small frontend so it is just a matter of choosing the files and an execute button (perhaps add a config panel)

anyone interested?... anyone already uses this program?

---

### Post by barney_1 on 2007-03-11
You might look into making a plugin for Amarok or Rhythm box.  That is something that has potential for a lot more use than a standalone frontend.  Cool project though, good luck!

---

### Post by Takmadeus on 2007-03-11
Well.... I then shall try once I finish the frontend.... gotta learn the rythmbox or amarok api first ;)

---

### Post by Takmadeus on 2007-03-15
OK.... here's an update... I already started the frontend and now I have the credits and the file chooser and the execute button... so practically you may say that it is already done.... yet I would like to choose multiple files at once and to have the config window ready before release..... yet I am also considering to migrate to another GUI designer such as Gazpacho.... but I must learn to use it before.... any help like a tutorial or some examples on using gazpacho are welcome ;)

---

### Post by Takmadeus on 2007-03-17
sorry for reposting but can any of you help me?

---

### Post by Takmadeus on 2007-03-25
I have a question and it is regarding Nautilus - actions...

I was trying to make a context launcher for a2mp3, yet I could not do it fine....

can someone check it out and correct it as needed?

---

### Post by ugm6hr on 2007-07-09
This is a great idea.  Did you ever get it finished?

I've just discovered a2mp3 (in Synaptic) - it seems to automatically chose an appropriate bitrate for the mp3, and sounds OK (to a non-expert with standard Walkman headphones) even if changing bitrate from mp3 to mp3.  I'm hoping it will add about an extra 40% storage capacity  (in terms of tracks) on my (flash memory) mp3 player.

To save the Terminal typing, I have managed to integrate it into Thunar (in Xubuntu):
Edit->Configure Custom Actions
Command: a2mp3 %F
File pattern: *
Appears if...: Audio files

As default saves to same file name in ~/mp3tmp, which is acceptable for now.  Does seem to suggest that it can be edited with option "a2mp3 *-d DIRECTORY* %F" - be nice if it could ask where to save to...

a2mp3 sometimes messes up the id3 tags - so id3v2 (also in Synaptic) allows a fix - also integrated into Thunar right-click:
Command: id3v2 -a "ARTIST" -A "ALBUM" %F
File pattern: *.mp3
Appears if...: Audio files

Again - be nice if it would ask what the ARTIST and ALBUM are with a GUI interface, but I can cope with having to edit the Thunar Custom Action each time.

---

### Post by Takmadeus on 2007-07-14
Excellent.... I am glad to see that someone finally put some interest :p

Anyway.... as far as I go I got this frontend made...

it is pretty rudimentary and it is programmed in GAMBAS (so far the only programming language I get to understand a bit :P) but for now it should get the work done..

The is one serious problem though, I haven't found any way for GAMBAS to allow me to select more than one file at the time, so I would appreciate some help...

And if anyone wants to help, and preferably knows how to code, some rewrite in another language would be much appreciated. Meanwhile I'll keep on looking around so I get the info I need to improve this partial release. Also, let me thank you ugm6hr for your suggestions, I'll look for a way to add them, and I hope I get it done anytime soon ;)

By the way, I will add the sources of the program in case someone wants to play with them ;)

---

### Post by Takmadeus on 2007-07-18
Well I hope this serves as a bump for this thread, plus I wanna know what do you think about the sources I posted earlier.

I want to make an open invitation as well for someone who knows how to code (no matter the language as long as it allows to make GUIs) to help us in this tiny simple project.

Thanks in advance ;)

---

### Post by bradleyd on 2007-07-18
just came across your post, are you still interested in working on a front end?

---

### Post by Takmadeus on 2007-07-19
Quite indeed but I have proved unworthy of doing it since my programming skills are not seeming to get better which is a shame. Plus due to real life events (like me entering a new semester in my career) I am left with no time for learning to code. It is a shame, yet I wouldn't like the idea to perish so I am making an invitation so someone takes the idea and turns it into something solid. Given the case that someone wants to take it, then just contact me via this thread and we will discuss the details :)

Thanks in advance ;)

---

### Post by bradleyd on 2007-07-19
This is just a quick look at the ui. It is done in python and wxWidgets. Or we could do it in C and Gtk+.
What do you think?

---

### Post by bradleyd on 2007-07-19
ok forget the first ui. I changed it. I ended up writing it in python. I need your help on one issue. a2mp3 can use the -d flag to output to a different directory(default=/home/user/mp3temp)I put a button for the user to select either just a directory(which then populates a listbox with all the files in directory, which the user then selects the desired files) or the button opens a files select dialog that lets the user select only the files they like, then that selection populates the the listbox. However the method to used to get the list of files to convert and normalize, the user then must select all the files in the listbox and then push a button on the tool bar to convert then place files in default directory or the directory the user chooses. So which method do you like? Files selection or Folder selection?
p.s. the modified ui.
Brad

---

### Post by Takmadeus on 2007-07-20
Files selection is way more practical ;)

Thanks man! I cannot wait to try it! ;)

---

### Post by bradleyd on 2007-07-20
Ok this is just a beta version. Download, untar folder. from the command line type(from within folder)```
./a2mp33.py
```
Now that the ui is up, first you must select a directory to search for mp3 or oggs(a2mp3 only supports these 2 formats)by pressing the red folder. When the file selection dialog pops up, use shif key or ctrl key to select one or multiple audio files and click open. Now you can then pick the directory where the files will be outputted by clicking the output button.(the default is /home/user/mp3tmp) The selected files will now show up in the listbox area. You must select all the files you wish to convert.(you can use the shift and ctrl keys) Then push the speaker to convert the selected songs to output directory.
When this occurs, the application appears to be frozen. This is ok, I was having trouble forking  the process and being able to tell when a2mp3 was done. I will figure this out later( I hope), but for now we need to know when the process is finished. As soon as the conversion is done the application becomes responsive again. Also if you minimize it while it is converting the ui will become unreadable. As soon as the process is finished it will redraw itself. Right know the application spawns a different a2mp3 process for each file selected to convert, this should speed up a huge file selection. This may cause problems on slower machines, dont know yet.
Ok now what I think we should add or not add:
[LIST]
[*]play selected song for test
[*]search folders for music
[*]feedback from stdout pipe for process info
[*]Progressbar?
[/LIST]
All of these need your input, I want to add some features but not over due it.
p.s. The screwdriver icon selects all files in listbox.
Let me know what you think so far.
Brad

---

### Post by Takmadeus on 2007-07-21
> **bradleyd said:**
> Ok this is just a beta version. Download, untar folder. from the command line type(from within folder)```
./a2mp33.py
```
Now that the ui is up, first you must select a directory to search for mp3 or oggs(a2mp3 only supports these 2 formats)by pressing the red folder. When the file selection dialog pops up, use shif key or ctrl key to select one or multiple audio files and click open. Now you can then pick the directory where the files will be outputted by clicking the output button.(the default is /home/user/mp3tmp) The selected files will now show up in the listbox area. You must select all the files you wish to convert.(you can use the shift and ctrl keys) Then push the speaker to convert the selected songs to output directory.
When this occurs, the application appears to be frozen. This is ok, I was having trouble forking  the process and being able to tell when a2mp3 was done. I will figure this out later( I hope), but for now we need to know when the process is finished. As soon as the conversion is done the application becomes responsive again. Also if you minimize it while it is converting the ui will become unreadable. As soon as the process is finished it will redraw itself. Right know the application spawns a different a2mp3 process for each file selected to convert, this should speed up a huge file selection. This may cause problems on slower machines, dont know yet.
Ok now what I think we should add or not add:
[LIST]
[*]play selected song for test
[*]search folders for music
[*]feedback from stdout pipe for process info
[*]Progressbar?
[/LIST]
All of these need your input, I want to add some features but not over due it.
p.s. The screwdriver icon selects all files in listbox.
Let me know what you think so far.
Brad

I love it.... yet there are some problems

```
Traceback (most recent call last):
  File "/home/takmadeus/Paquetes/a2mp3/a2mp33.py", line 111, in OnAdvanced
    self.list_box_1.SelectAll()       
AttributeError: 'ListBox' object has no attribute 'SelectAll':guitar:

```
 
it appears when I choose de "!" icon

else is just fine.... I hope there was any means to add a progress bar but I guesss it is inherent to the program



Another problem is as folllows:

when you choose a file that has spaces, it interprets it as for example 

/media/hda5/My_Music/Guilty gear XX/Feel a fear.mp3

while the appropiate is:

"/media/hda5/My_Music/Guilty gear XX/Feel a fear.mp3" (with commas)

that is meant so a2mp3 interprets it as a file with spaces else it will pop this error for example:


```
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
WARN: file has no extension, skipping
Error opening MP3: Fear.mp3: No such file or directory
Could not find "Fear.mp3".
WARN: Problems encoding file "Fear.mp3" with lame
18060

```

I hope you understand,other than that you captured the idea in the frontend ;) thanks!

---

### Post by bradleyd on 2007-07-21
Forgot to mention about the spaces. Going to have figure out a way to strip out spaces, then pass it to a2mp3. The problem is with that, if you do not own the file we will run into permission problems. I had fixed the select all button(!, not the perm icon))but uploaded you the older version, sorry. It works now. I have included the fixed version.  I am working on a progress bar, the problem I am running into is calculating the song size and predicting the length of  time to convert track. I guess I could do a while loop incrementing  until the pid is destroyed. It is a lot trickier than it sounds(at least for me) I am still playing with a way to subprocess or thread the a2mp3 call so the gui does not freeze, and still give feedback to the user.  It is still a work in progress. What else do you think we need? Also if you have a better idea on the spaces in the songs, I would love the help:) I am thinking of just stripping out all spaces and replacing them with underscores?Also maybe  a popup dialog when the song finishes?
Brad

---

### Post by Takmadeus on 2007-07-27
tried it once more.... still the probelm with the spaces.... yet everything else works just fine ;) great job!.... I wish I could help you to solve the spaces thingy :(

---

### Post by bradleyd on 2007-07-27
I guess I should have posted better. I have still not fixed the space problem.(I got busy with work) I am going to work on subprocess problem and space's problem this weekend, hopefully. 
Brad

---

### Post by Takmadeus on 2007-07-30
Don't worry man, you are doing great!

---

### Post by ProsperB on 2007-12-28
Sorry to bump this, but I'm interested in the results of your work.  Did anything come out of it with all off the bugs fixed ?
Thanks a lot in advance.

---

### Post by bradleyd on 2007-12-28
yes, I had done a better version with most of the bugs fixed. Did not post it, work has been crazy! It is on another box at home. When I get homee I will post what I have. Sometime tonight.
Brad

---

### Post by bradleyd on 2008-01-01
Sorry about the delay, work and the holidays have kept me busy. Anyway here is a better version from the first. Most of the bugs should be fixed now. Please fix it in anyway you like. The space problem in the song title should be fixed. It makes a copy of the selected songs and strips out spaces and replaces them with a dash. Then it  feeds the copy's to a2mp3 to be normalized. I also added a feature to convert wav to mp3 via lame. I did this cause when I was testing all I had was wav files around so I kept having to convert them to mp3. I just thought adding the convert would be a nice feature:). I did not add any lame flags, just -h for high quality. Probably better to add a choice for selecting flags for lame down the road. just unpack it and run ```
python ./pyA2mp3.py
``` and the rest should be self explanatory.
Hope this is what you were looking for. 
Brad

---

### Post by hello11 on 2008-01-03
Thanks!

---

### Post by ProsperB on 2008-01-03
@bradleyd

hello11 beat me to it, but since he says thanks, you've got mine too :) We're both on the Dutch Ubuntu-forum, he yelped and I found this thread.  Keep up the good work !

---

### Post by bradleyd on 2008-01-03
no problem, glad I could help.
One thing, if you are doing a huge batch of songs there is no real way of telling when it finishes.(there should be a text message in the status bar telling you it is done)but this is not fool proof. when I get sometime, or if someone else would, need to add a progress bar to know when the process is over. Besides that let me know if you find anything else.
Brad

---

### Post by Takmadeus on 2008-01-04
well... took me a while but by using Kommander editor I came up with a frontend for kde users... IMO it is neat because its simple and functional, any ideas well, just tell me in this thread ;)

I also want to give thanks to Bradley, he did a magnificent job at doing this frontend ;)


BTW mine just needs kommander executor... present in most kde releases ;)... if anyone knows how to turn it into a binary static file, I would appreciate it ;)

---

### Post by bradleyd on 2008-01-04
Takmadeus,
 I will check it out when I get home. I do not have KDE at work, only gnome. I was going to mention that you could use the frontend I did on any platform as long as they had wxlibs. I was thinking of making a binary  with all the python and wxwidgets libs already compiled into it, so you would have just a single binary that would work on almost any platform:)

I am not familiar with komander, I will definitely have to take a look at it, sound interesting.

Thanks for starting this whole thing, it was fun. We should do this again.
Brad

---

### Post by Takmadeus on 2008-01-04
OK... doing a progress bar or a time estimated clock is very very difficult since the script (a2mp3) does not provide any signal of progress... unless of course someone steps up and modifies the script so it includes it... then it should be easy (at least in kommander)

As for kommander... i cannot believe how ridiculously easy is to make a frontend.... it is so easy that it is difficult to understand how easy it can be.... 

And as for other CLI programs well... you just tell me which other useful CLI programs are around and I will try my best. For now my next program to frontend will be VisualBoyAdvance emulator (none of the frontends satisfy me :))

so any ideas are welcome. :)


Edit: BTW, just finished a youtube-dl frontend... hope you like it... any ideas please PM me or reply in this thread ;)

---

### Post by bradleyd on 2008-01-04
> OK... doing a progress bar or a time estimated clock is very very difficult since the script (a2mp3) does not provide any signal of progress
a2mp3 has a pid when it is being run. I was thinking of putting a watcher thread to keep watching for the pid to die, then display job done in the status bar.. For the taskbar,  you would have to take an estimate of a average song to normalize, then do the math for how many songs in the list. This should give you an estimate on the length of time to increment the taskbar with. Not very elegant but all I could think of right now.

---

### Post by Takmadeus on 2008-01-04
hmmm interesting suggestions... BTW, i have a problem.... i cannot seem to figure out how to pass stdout as a veriable for kommander to read, so I could put the messages of stdout in a status bar... anyone reading this can help me?

---

### Post by bradleyd on 2008-01-04
I am putting kde and kommander on another machine to play with it.
How does kommander(or is it Qt, or C++) handle strings? Show us what you have so far for code, and maybe someone can help:)

---

### Post by Takmadeus on 2008-01-05
OK... here's what I got.... managed to pass stdout to a file (/tmp/ydf.txt)... now it is just a matter of Statusbar.setText (pretty selfexplanatory property :p) to cat /tmp/ydf.txt, yet the problem is that it prints an error in stderr (about a recursive callback, which i do not understand and do not know how to fix :p

I'll post the script in a moment ;)

---

### Post by bradleyd on 2008-01-05
any reason you are dumping it to a file? You are catting  the file to read it back. Is there a open file function. In python you can open a file then assign the results of a readlines to a object. Then self.StatusBar.SetText(object) Something like this:
```
f = open(filename, "r")
text = f.readlines()
print text
```
 I am still reading kommanders scritping language, I did find this:
```
@forEach(i, @File.read(.ink))
         @setGlobal(curr, "@i")
         @ScriptObject6.execute
@end> 
#ScriptObject6 contains consecutive if statements like
@if(@String.contains(@global(curr), "Black"))
  @ProgressBar1.setText(@String.remove(@String.right(@global(curr), 3), " ")) 
@endif
```Looks like they a reading a file line by line and putting the results into a global object called curr. Then if curr has the string "black" in it, set the progressbar to the object curr.
I did find this at tge last minute,[http://docs.kde.org/stable/en/kdewebdev/kommander/specials.html](http://docs.kde.org/stable/en/kdewebdev/kommander/specials.html)
Scroll down to you see File Function group and String.
I hope that helps.
Brad

---

### Post by Takmadeus on 2008-01-06
> **bradleyd said:**
> any reason you are dumping it to a file? You are catting  the file to read it back. Is there a open file function. In python you can open a file then assign the results of a readlines to a object. Then self.StatusBar.SetText(object) Something like this:
```
f = open(filename, "r")
text = f.readlines()
print text
```
 I am still reading kommanders scritping language, I did find this:
```
@forEach(i, @File.read(.ink))
         @setGlobal(curr, "@i")
         @ScriptObject6.execute
@end> 
#ScriptObject6 contains consecutive if statements like
@if(@String.contains(@global(curr), "Black"))
  @ProgressBar1.setText(@String.remove(@String.right(@global(curr), 3), " ")) 
@endif
```Looks like they a reading a file line by line and putting the results into a global object called curr. Then if curr has the string "black" in it, set the progressbar to the object curr.
I did find this at tge last minute,[http://docs.kde.org/stable/en/kdewebdev/kommander/specials.html](http://docs.kde.org/stable/en/kdewebdev/kommander/specials.html)
Scroll down to you see File Function group and String.
I hope that helps.
Brad

lol.... sorry, but i do not understand anything of that :p... I am stil a newbie :p....- plus i am not good at understanding (let alone using) if cycles :p


I know, I know... I still have a long way to go :p that's why I am gonna begin using hacketyhack :p

---

### Post by bradleyd on 2008-01-06
I am still a hack also, don't feel bad:) Post what you have so far for code and see if we can figure it out.

---

### Post by Takmadeus on 2008-01-08
OK, here it is ;)

---

