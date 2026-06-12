---
title: "HOWTO: Current playing song from XMMS in status message, using Gaim 2.0 from CVS"
date: 2006-01-29
forum: Outdated Tutorials &amp; Tips
---

### Post by louis_nichols on 2006-01-29
Hi everybody! It's trendy nowadays to have the song that you listen show in the status of your messenger account. So, I'm writing this little howto, which probably won't contain very new stuff for many of you, but stuff that some might not know. So... Here we go.

1. First of all, follow this great HOWTO to get your Gaim 2.0 up and running

[http://ubuntuforums.org/showthread.php?t=100899](http://ubuntuforums.org/showthread.php?t=100899)

2. Next, you need autoprofile. I compiled a working binary, which I am attaching here. It's compiled against today's Gaim CVS but I don't think they will make changes that would cause it not to work anytime soon. I'm not a very experienced programmer, so I had to disable the HTTP component feature, which we don't need. After downloading it, install it:

```
mkdir ~/.gaim/plugins/
cd <directory where you downloaded autoprofile.so.zip>
unzip autoprofile.so.zip -d ~/.gaim/plugins/
```

3. Now, with xmms. We will use the song_change plugin, which performs a shell action on various events in XMMS. So, go to XMMS/Preferences/General plugins. Select SongChange, click enable, and then configure. In the first edit box: "shell-command to run when XMMS starts a new song" insert

```
echo "%n" > "<path to home folder>/xmms_song.txt"
```

Then click ok for the plugin settings and then apply in the XMMS preferences window. This plugin comes with standard XMMS.

4. Now... Restart Gaim. Go to the plugins screen (right click on the tray icon, select plugins). There, enable autoprofile, and then click "configure plugin". In the autoprofile configuration window, go to "Output text" tab and click Add. In the window that appears, enter the title "XMMS song info" then click OK. Now you will have this option among the Output text entries. Select it and click "Edit Text". The only thing you really need to enter in the big edit box is %x , which will be replaced with the song title but it would be nice to enter something customized, like: "Now listenning to ..:: %x ::.." or whatever you like.

5. Last step... In the autoprofile settings window, go to "Component settings" tab then under component list choose option "Text file/Songs" and you will have a browse button which you will use to select the file xmms_song.txt from your home directory. Make sure to change the song in XMMS at least once before this, to cause XMMS to create the file; otherwise, of course, it won't be there.

That's pretty much it. To enable the status, open the buddy list window of Gaim,go to Tools/Autoprofile/Away and in the window that shows up select option "XMMS song info" then click "use'. Et voila! The plugin will refresh the status message at intervals which you can select in the plugin configuration screen, under behavior tab. I use 1 minute, which is the shortest interval. It won't be instantaneous, but it will do (I doubt any of you have songs shorter than 1 minute :p).

Tip: You can also use, let's say, "context specifc" text if you like. What I do is, under the Output text of autoprofile, enter

Now listenning to ..:: %x ::.. %a

Then, when I enable the away message, there is a small edit box there where I can enter the message which will replace %a. So for example, by entering "and studying" I will have the status:

Now listenning to ..:: song title ::.. and studying

If you enter nothing, then it will be just Now listenning to ..:: song title ::..


Well... that's it for the first howto I ever write. Hope someone will find it useful. I am of course open to any criticism and suggestions, so, please, "don't hold back" (yes, that is from a song by The Chemical Brothers). :)

---

### Post by limit223 on 2006-02-03
Thank you for your guide. 
It works!

---

### Post by louis_nichols on 2006-02-05
:)

You're wellcome!

---

### Post by Fab on 2006-02-06
Works pretty well so far, I got one problem though... Whenever the string from xmms contains a german "umlaut" (e.g. ü), this one gets transfered into the text file in iso encoding, and gaim then puts it in accounts.xml, which uses utf-8. It hangs at displaying the previous song (even after the text file changes content to the next track), and the next time i start gaim, it can't read accounts.xml, and I have to manually remove all the wrong umlauts in there. Is their a way to transform them to utf-8, or maybe, change from ö to oe, ü to ue, etc... (I though about some sed magic, but can't get it to work properly ;P)

Regards

---

### Post by louis_nichols on 2006-02-06
I know what you're talking about. I'll look into it, too. I know bmp has an option among the preferences to convert all titles to UTF-8, but it seems XMMS doesn't. :(

There's gotta be a solution, it just doesn't pop into mind right now.

---

### Post by louis_nichols on 2006-02-06
Well... here's what I got so far.

I think the answer is the iconv utiity. This would mean writing in song_change something like:

```
echo "%n" > "<path to home folder>/xmms_song.txt"; iconv -f ISO-8859-1 -t UTF-8 "<path to home folder>/xmms_song.txt" -o "<path to home folder>/xmms_song.txt"
```

But... I couldn't get it to work. I used the above command, but, for an unknown reason it will leave the file empty. Iconv will do that even in console: running

```
iconv -f ISO-8859-1 -t UTF-8 "<path to home folder>/xmms_song.txt"
``` will display the result in console, but running

```
iconv -f ISO-8859-1 -t UTF-8 "<path to home folder>/xmms_song.txt" -o "<path to home folder>/xmms_song.txt"
```
will leave the file empty. I don't understand this, but I'll do some more research.

Another thing is that not even iconv gets things completely right. It may not replace ü with an u, as you would probably like.

Edit: well, I didn't think it would be that, but it was: the filename must be different. so you would have to do something like:

```
echo "%n" > "<path to home folder>/xmms_song_temp.txt"; iconv -f ISO-8859-1 -t UTF-8 "<path to home folder>/xmms_song_temp.txt" -o "<path to home folder>/xmms_song.txt
```

the ü and u issue I think will remain, though. But at least it won't freeze your gaim. Please get back and tell us if this worked. :)

---

### Post by LordBug on 2006-02-06
If you wanted to keep it clean, you should be able to tack an RM command on the end of all that to delete the temp file:

```

echo "%n" > "<path to home folder>/xmms_song_temp.txt"; iconv -f ISO-8859-1 -t UTF-8 "<path to home folder>/xmms_song_temp.txt" -o "<path to home folder>/xmms_song.txt; rm "<path to home folder>/xmms_song_temp.txt"

```

---

### Post by Fab on 2006-02-06
I managed to do it by using ```
echo "%n" |  iconv -f ISO-8859-15 -t UTF-8 > "/home/xyz/.current-song"
``` as song change code :) thanks for the right direction ;)

[QUOTE=louis_nichols]
the ü and u issue I think will remain, though. But at least it won't freeze your gaim. Please get back and tell as if this worked. :)[/QUOTE]

well, it does correctly transform iso ü's to utf ü's now, and gaim will display them  correctly too. i should have been more clearer on the hang stuff though, it doesn't hang gaim as whole, but the status is stuck at one song before the umlauted one, and wont start after closing. (no matter what song i was playing last, if at one point when auto profile read the file it contained an iso umlaut, the accounts.xml file gets corrupted till manually fixing it!)

regards \\:D/

---

### Post by louis_nichols on 2006-02-06
Really cool, then! :D Glad it's ok now. I'm not good with encodings (in fact I am quite a big newb with Linux as a  whole, and encoding problems don't really come to the surface in windoze), so I'm just glad that my playlist doesn't have any special characters. But, in order to complete the howto: how exactly does one know that there it's ISO-8859-x and not ISO-8859-y? I tried pretty much all that might apply to romanian special characters, but didn't get good results, such as an a instead of an &#259; or â.

LordBug: thanks for the input. I guess I didn't do it that way because the file would be re-created and reused anyway. But pipelining is the way to go, as Fab has shown. I had tried that, but iconv seemed to always require a file as input. So I learn something new every day. :)

---

### Post by DJ_Tobias on 2006-02-07
The plugin is not listed in my gaim plugin menu, but i extracted it to where you stated, as well as /usr/local/lib/gaim, but still nothing, any idea why?

---

### Post by louis_nichols on 2006-02-07
[QUOTE=DJ_Tobias]The plugin is not listed in my gaim plugin menu, but i extracted it to where you stated, as well as /usr/local/lib/gaim, but still nothing, any idea why?[/QUOTE]

Try /usr/local/lib/gaim or ~/.gaim/plugins or /usr/local/lib/gaim/plugins. ;)

Edit: I first wrote /usr/lib/gaim/plugins but that doesn't work. The ones above are sure to work, though.

---

### Post by louis_nichols on 2006-02-07
Sorry, I missread your post, DJ_Tobias. The only thing that comes to mind is an incompatibility in API, although that would be odd. When did you compile your gaim?

---

### Post by DJ_Tobias on 2006-02-08
i complied it yesterday from the link you stated. i did everything exactly as you said :) but no go :-/

---

### Post by louis_nichols on 2006-02-08
I'm trully sorry, but I can think of no explanation to this. The only thing I can think of right now, as a suggestion, would be that you compile autoprofile yourself. It's not difficult. Just follow the instructions. If you run into problems, I've been there and I believe I can help with that. You can find the source here:

[http://hkn.eecs.berkeley.edu/~casey/autoprofile/](http://hkn.eecs.berkeley.edu/~casey/autoprofile/)

---

### Post by dude2425 on 2006-04-16
this took me all freaking day to figure out. I've never programed in python before, but I thought I'd give it a shot and write something up for rhythmbox. my very first program.
Here's how to get it running.
Save this as `/usr/local/bin/nowListening.py`
```
#!/usr/bin/env python
import dbus
#change the path here to suit your needs, you will definitely not need /home/cjhard
path = '/home/cjhard/playing'
bus = dbus.SessionBus()
rbplayerobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')
rbplayer = dbus.Interface(rbplayerobj, 'org.gnome.Rhythmbox.Player') 
rbshellobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Shell')
rbshell = dbus.Interface(rbshellobj, 'org.gnome.Rhythmbox.Shell') 
data = rbshell.getSongProperties(rbplayer.getPlayingUri())
title = data['title']
artist = data['artist']
album = data['album']
duration = data['duration']
minute = 0
while duration >= 60:
    minute += 1
    duration -= 60
duration_show = '%d:' % minute
if duration < 10:
    duration_show += '0' + str(duration)
else:
    duration_show += str(duration)
elapsed = rbplayer.getElapsed()
orig = elapsed
minute = 0
while elapsed >= 60:
    minute += 1
    elapsed -= 60
elapsed_show = '%d:' % minute
if elapsed < 10:
    elapsed_show += '0' + str(elapsed)
else:
    elapsed_show += str(elapsed)
#change the text here to suit your needs. This is how I like mine:
output = 'Now Playing \"' + title + '\"' + ' by ' + artist +' (' + elapsed_show + '/' + duration_show + ')'
#print output
f=open(path, 'w')
output = output.encode("UTF-8")
f.write(output)

``` give it executable permisions
$ sudo chown +x /usr/local/bin/nowListening
open autoprofile prefs and set the executable component to run /usr/local/bin/nowPlaying
once it runs for the first time it will create your text file.
You need to have an %e somewhere in your output text before you put %x for your text file. I set mine to %e%x at the very top.
Now go to the Text File / Songs component, and enter the path you specified at the very begining of the script.
It first my idea was to just use dbus to set my status message to my currently playing song in rhythmbox, and it was going to use a bash script instead of python, but my project got carried away and I couldn't figure out how to get dbus to send the message to gaim to set the status (I'd prefer to be able to see available status being set, not just away). Autoprofile seems a descent alternative till I can figure that out.
Hope you enjoy my little script. I hope to figure out how to work with dbus so I can implement my original idea and skip autoprofile (it seems very unstable in gaim2.0beta3 for some reason, and crashes when I'm fiddling with settings). If anybody wants to give me a little help, a push in the right direction, please by all means, email me, IM me, anything.

---

### Post by louis_nichols on 2006-04-16
Pretty cool, man! thanks for the effort!

Myself, i don't use rhythmbox, but I bet there are tons of ppl out there who will find it useful. Perhaps make a similar one for amarok, using the dcop interface, which is really simple and also has python bindings.

---

### Post by SomeoneWhoIsntMe on 2006-04-16
Could you make a guide to compile the plugin? I'm on 64-bit ubuntu, so the plugin doesn't work for me. Also, I'm pretty sure you don't need the <path to home directory>, you can just use $HOME

---

### Post by louis_nichols on 2006-04-16
[QUOTE=SomeoneWhoIsntMe]Could you make a guide to compile the plugin? I'm on 64-bit ubuntu, so the plugin doesn't work for me. Also, I'm pretty sure you don't need the <path to home directory>, you can just use $HOME[/QUOTE]

You mean autoprofile? Unfortunatelly, I don't have a 64bit machine, so I wouldn't know. I would look for help on [autoprofile's home page]("http://hkn.eecs.berkeley.edu/~casey/autoprofile/").

The $HOME placeholder, I don't know if it would work, with a python script. Though I'm sure there are python funtions somewhere that can return the home directory.

---

### Post by dude2425 on 2006-04-16
hmm, quite an annoying bug I've noticed with my script. If anybody knows any python, maybe could you help me with this
If gaim is running, and rhythmbox isn't, every time autoprofile goes to update, it'll run the script, which launches rhythmbox if it's not running already. I don't know how to test to see if rhythmbox is running or not in python. I want to tell it to exit if it's not running, and if it's found running to just continue with the script.

---

### Post by Haegin on 2006-04-17
Ok, I have just written a quick perl script to do the same for mpd. It requires you to install mpc but if you are using mpd then you will probably have mpc anyway.
Just copy the script below into a file
Save it as something (mpcTitleArtist.plx for example)
Make it executable ```
chmod +x mpcTitleArtist.plx
```
Place it in /usr/local/bin/
In autoprofile:
1. Include %e where you want the "title - artist" included.
2. In the component settings tab set the executable to be "/usr/local/bin/mpcTitleArtist.plx"

The script:
```

#!/usr/bin/perl
use warnings;
$mpc = `mpc`; # Gets the output of the mpc command
@mpcDetails = split(/\n/,$mpc); # Splits the output of mpc command into an array with one line per list value
$_ = $mpcDetails[0]; # Set the first line of mpc into the $_ variable for later reg exp manipulation
#if (/ - /){ # splits the title and the artist into seperate variables
#	$artist = $`;
#	$title = $';
#	}
print "$mpcDetails[0]\n"; # Prints out <artist> - <title>
#print "Artist: $artist\n"; # Prints out Artist: <artist>
#print "Title: $title\n" # Prints out Title: Title;

```
If mpd is not playing then it will say something like "volume:100%   repeat: off   random: on"

---

### Post by louis_nichols on 2006-04-17
Well, we seem to be getting somewhere. :)

Here's what I've come up with: current playing song from amarok in autoprofile, a VERY easy way. Steps:

1. Open autoprofile configuration and go to "component settings". Choose "executable" and paste in there
```
dcop amarok player nowPlaying
```
2. Go to output text and make a new entry contining %e
3. Activate the said away message.
4. That's it!

So... To all that have contributed to this thread, I have a suggestion: starting a new thread, with methods for various players. Especially since the cvs thing is not the point, obviously, on the long run.

Then, the first post will always be updated to contain all the methods posted throughout the thread. I can take care of the updating and all, but, since you are the authors of your own scripts, I need your approval for this. Needless to say, every method will be credited to the author.

---

### Post by Indian Stallion on 2006-06-20
[QUOTE=louis_nichols]
Here's what I've come up with: current playing song from amarok in autoprofile, a VERY easy way. Steps:

1. Open autoprofile configuration and go to "component settings". Choose "executable" and paste in there
```
dcop amarok player nowPlaying
```
2. Go to output text and make a new entry contining %e
3. Activate the said away message.
[/QUOTE]

Thanks, this makes it really simple. However I have a question, the info only appears when I choose away from the tools>autoprofile menu. Is there a way to make it appear even when I am available ? Set as default profile option doesn't work for me.

---

### Post by louis_nichols on 2006-06-20
Well, if I understand your question well, then the last version of autoprofile might be your answer. It took me a while to figure it out (dunno why, because it's explained right there ](*,) ).

It has placeholders. So for example you enter for autoprofile text *dcop amarok player nowPlaying* and it will have the placeholder [amarok_info] or whatever you choose. Then, you can use this anywhere you want in away or available messages and it will be replaced with the song info. So for example you can write *Now buzin [amarok_info]* in the status window.

This is possible with previous versions of autoprofile too, but this seems much easier.

---

### Post by dude2425 on 2006-06-21
[quote=louis_nichols]Well, if I understand your question well, then the last version of autoprofile might be your answer. It took me a while to figure it out (dunno why, because it's explained right there ](*,) ).

It has placeholders. So for example you enter for autoprofile text *dcop amarok player nowPlaying* and it will have the placeholder [amarok_info] or whatever you choose. Then, you can use this anywhere you want in away or available messages and it will be replaced with the song info. So for example you can write *Now buzin [amarok_info]* in the status window.

This is possible with previous versions of autoprofile too, but this seems much easier.[/quote]
I'm having dificulty finding this feature :(

I fixed up and updated my little python script
```
#!/usr/bin/env python
import dbus
import os
if os.system("ps -A|grep rhythmbox >/dev/null") != 256:
    bus = dbus.SessionBus()
    rbplayerobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')
    rbplayer = dbus.Interface(rbplayerobj, 'org.gnome.Rhythmbox.Player')
    playing = rbplayer.getPlaying()
    if playing == True:
        rbshellobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Shell')
        rbshell = dbus.Interface(rbshellobj, 'org.gnome.Rhythmbox.Shell')
        data = rbshell.getSongProperties(rbplayer.getPlayingUri())

        title = data['title']
        artist = data['artist']
        album = data['album']
        duration = data['duration']
        minute = 0
        while duration >= 60:
            minute += 1
            duration -= 60

        duration_show = '%d:' % minute
        if duration < 10:
            duration_show += '0' + str(duration)
        else:
            duration_show += str(duration)

        elapsed = rbplayer.getElapsed()
#        orig = elapsed
        minute = 0
        while elapsed >= 60:
            minute += 1
            elapsed -= 60

        elapsed_show = '%d:' % minute
        if elapsed < 10:
            elapsed_show += '0' + str(elapsed)
        else:
            elapsed_show += str(elapsed)

        # +1 because rhythmbox updates playcount after song is done playing, and I want to include current play in playcount.
        if data['play-count'] + 1 >= 2:
            playcount = str(data['play-count'] + 1)
            output = 'Now playing \"' + title + '\" by ' + artist + ' (' + elapsed_show + ' of ' + duration_show + ')\n\tThis song has been played ' + playcount + ' times.'
        else:
            output = 'Now playing \"' + title + '\" by ' + artist + ' (' + elapsed_show + ' of ' + duration_show + ')'
    else:
        output = "\tRhythmbox is not playing right now"
else:
    output = "\tRhythmbox is not running right now"
    # Because it's UTF-8 or bust
print output.encode("UTF-8")

```
Just put it in /usr/local/bin/nowListening. This one you just need to add executable component, you don't need the text file / songs component. It also won't force rhythmbox to open if it's not already opened, although I'm sure there has to be a better/more efficient way of doing it than I've done it here.

I've also found another script (read:not mine) somewhere that I can't remember now (sorry, if you know please contact me so I can give credit where it's due) that is supposed to set the friendly names in MSN and set the available/away messages in everything else to your currently playing info in rhythmbox, but it just doesn't work for some reason. If anybody knows anything about gaim's dbus interface, please please please help me get this to work
```
#!/usr/bin/python
# Update gaim messages and friendly names with information for currently playing song

import dbus
import dbus.glib
import gobject

class IMAccount: # empty class to put account variales into
    pass

bus = dbus.SessionBus()
rbshellobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Shell')
rbshell = dbus.Interface(rbshellobj, 'org.gnome.Rhythmbox.Shell')
rbplayerobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')
rbplayer = dbus.Interface(rbplayerobj, 'org.gnome.Rhythmbox.Player')
gaimobj = bus.get_object('net.sf.gaim.GaimService', '/net/sf/gaim/GaimObject')
gaim = dbus.Interface(gaimobj, 'net.sf.gaim.GaimInterface')

def playing_uri_changed(uri):
    props = rbshell.getSongProperties(uri)
    value = 'Now playing \"' + props['title'] + '\" by ' + props['artist']
#    print value
    accounts = gaim.GaimAccountsGetAllActive()
    for account in accounts:
#        print account
        protocol = gaim.GaimAccountGetProtocolId(account)
#        print protocol
        status = gaim.GaimAccountGetActiveStatus(account)
        status_id = gaim.GaimStatusTypeGetId(gaim.GaimStatusGetType(gaim.GaimAccountGetActiveStatus(account)))
        if (protocol == 'prpl-oscar') | (protocol == 'prpl-jabber'): # set the away message for oscar and jabber
            message = gaim.GaimStatusGetAttrString(status, 'message')
#            print message
            if message.find("Now Playing") != -1:
                message = message[:message.find("Now Playing")]

            gaim.GaimStatusSetAttrString(status, 'message', message + value)
            message = gaim.GaimStatusGetAttrString(status, 'message')
#            print message
        elif protocol == 'prpl-msn': # set the friendly name for msn
            connection = gaim.GaimAccountGetConnection(account)
            message = gaim.GaimConnectionGetDisplayName(connection)
#            print message
            if message.find("Now Playing") != -1:
                message = message[:message.find("Now Playing")]

            gaim.GaimConnectionSetDisplayName(connection, message + value)

#rbplayer.connect_to_signal('playingUriChanged', playing_uri_changed)
bus.add_signal_receiver(playing_uri_changed,
                        dbus_interface = "org.gnome.Rhythmbox.Player",
                        signal_name = "playingUriChanged")

loop = gobject.MainLoop()
loop.run()

```
I've done everything I could think of and nothing works for me :(

---

### Post by Indian Stallion on 2006-06-23
[QUOTE=louis_nichols]Well, if I understand your question well, then the last version of autoprofile might be your answer. It took me a while to figure it out (dunno why, because it's explained right there ](*,) ).

It has placeholders. So for example you enter for autoprofile text *dcop amarok player nowPlaying* and it will have the placeholder [amarok_info] or whatever you choose. Then, you can use this anywhere you want in away or available messages and it will be replaced with the song info. So for example you can write *Now buzin [amarok_info]* in the status window.

This is possible with previous versions of autoprofile too, but this seems much easier.[/QUOTE]

I am having problem finding this feature as well. Where exactly do you set/specify the placeholder?

---

### Post by sabitha on 2006-07-03
> 5. Last step... In the autoprofile settings window, go to "Component settings" tab then under component list choose option "Text file/Songs" and you will have a browse button which you will use to select the file xmms_song.txt from your home directory. Make sure to change the song in XMMS at least once before this, to cause XMMS to create the file; otherwise, of course, it won't be there.

sorry i dont know what is that mean xmms_song.txt, i create file first or what?
because i browse my home direktory and didnt find that file (xmms_song.txt)
if i create the file is that empty or what should i do ?
sorry for the languages

---

### Post by Indian Stallion on 2006-07-03
[QUOTE=sabitha]sorry i dont know what is that mean xmms_song.txt, i create file first or what?
because i browse my home direktory and didnt find that file (xmms_song.txt)
if i create the file is that empty or what should i do ?
sorry for the languages[/QUOTE]

Look at step 3, You need to configure your Song Change plugin in xmms, that plugin will generate the xmms_song.txt file. Play a song on xmms, the file should be created. Here it is again:

[QUOTE=louis_nichols]We will use the song_change plugin, which performs a shell action on various events in XMMS. So, go to XMMS/Preferences/General plugins. Select SongChange, click enable, and then configure. In the first edit box: "shell-command to run when XMMS starts a new song" insert

Code:

echo "%n" > "<path to home folder>/xmms_song.txt"
[/QUOTE]

---

### Post by sabitha on 2006-07-03
ok thanks ....
my fault i wrote this {echo "%n" > "</home/ubuntu>/xmms_song.txt"}
with < & > 
LOL
btw thanks again for help

---

### Post by sabitha on 2006-07-03
ok thanks ....
my fault i wrote this {echo "%n" > "</home/ubuntu>/xmms_song.txt"}
with "<" & ">" 
LOL
btw thanks again for help

---

### Post by st00ner on 2006-07-04
hi thank you for the great guide, but the plugin is not showing up after i copy it. I have checked and it is there, and i am running GAIM 2.0.0. Has anyone else had this problem

---

### Post by Sandlst on 2006-07-09
Hmm I'm running into a strange problem here with this.....I keep getting this error every time I try to toggle on auto-profile for my msn account:```
*** glibc detected *** double free or corruption (out): 0x08433210 ***
Aborted

``` Running Dapper with latest updates here, gaim version 2.0.0 beta3.  Any help would be greatly appreciated.

---

### Post by gschoper on 2006-08-20
> **Sandlst said:**
> Hmm I'm running into a strange problem here with this.....I keep getting this error every time I try to toggle on auto-profile for my msn account:```
*** glibc detected *** double free or corruption (out): 0x08433210 ***
Aborted

``` Running Dapper with latest updates here, gaim version 2.0.0 beta3.  Any help would be greatly appreciated.

I'm getting this error as well. Both with Gaim 2.0.0beta3 and beta3.1 from CVS.

---

### Post by attiliok on 2006-09-09
same error for me! :(

---

### Post by stainy on 2006-11-19
I'm running edgy, with Gaim 2.0.0beta3.1

Problem I get is gaim crashes out when I try and enable one of my msn profiles under the autoprofiler config.

Every time without fail.

Anyone have any ideas?

---

### Post by tomcheng76 on 2006-11-25
does it work with bmp?

and is it support unicode?

most of my song is not english :)

---

### Post by disc on 2006-11-30
> **stainy said:**
> I'm running edgy, with Gaim 2.0.0beta3.1

Problem I get is gaim crashes out when I try and enable one of my msn profiles under the autoprofiler config.

Every time without fail.

Anyone have any ideas?

I too am getting the same problem, everything else works fine. It doesn't crash the second I toggle, rather it crashes when I close the autoprofile window.

---

### Post by spx3 on 2006-12-12
i have tried the plugin too.
it crashed as you guys said but now its ok in the sense that
when i tools->autoprofile->edit user profile
i see my status with the music that should be put as status
but my status remains the same as before.
if i do tools->plugins->autoprofiler->configure->accounts->yahoo account->toggle auto-away or auto profile
none of them work as they should altough it constructs the away message
it never is able to activate it into gaim so that i can see it.
i have tried
 /away as auto-profiler suggests.
that doesnt work also

---

### Post by martibs on 2006-12-14
I'm using the beta5 release, I am unable to enable autoprofiler at all. It says I'm using gtk-gaim, and that it's supposed to run on gaim. I cannot compile the autoprofiler source, as there is no "plugins"-folder in the gaim2-beta5 source code.

---

### Post by louis_nichols on 2006-12-15
> **martibs said:**
> I'm using the beta5 release, I am unable to enable autoprofiler at all. It says I'm using gtk-gaim, and that it's supposed to run on gaim. I cannot compile the autoprofiler source, as there is no "plugins"-folder in the gaim2-beta5 source code.

Unfortunatelly, because of a change in API, autoprofile doesn't work with gaim beta4 and beta5. The official site says this will be solved, but as yet there is no solution.

---

### Post by adrianus on 2006-12-24
I am using Edgy and gaim 2.0.0beta5 (installed and compiled from source code with dbus support)
Since auto-profile currently is not working with the latest gaim beta I try to use gaim-remote and it works ! :)

In the Song Change plugin configuration in XMMS this is what I enter into the Command field 

gaim-remote setstatus?message="Listening to %s"

Of course this has not much option like auto-profile plugin, but this will have to do until auto-profile is updated to work with latest gaim beta

---

### Post by kapetanski on 2007-01-04
I tried this howto but when I logged into an aMSN account to check the away message coming from gaim there was only "away". But gaim itself gives the impression that the away message is used, this is strange. Is there an easy way to update the friendly name insead of the away message?

---

### Post by kapetanski on 2007-01-04
Well, I found this friendly name changer plugin, but I don't know how to enable it, I guess I must compile it, but how ;)

[http://www.bennee.com/~alex/software/perl/gaim_set_friendly.pl]("http://www.bennee.com/~alex/software/perl/gaim_set_friendly.pl")

---

### Post by kapetanski on 2007-01-04
Hmm, when i run gaim -d in terminal I get this error when loading the plugin, 

```
plugins: Loading saved plugin /home/beta/.gaim/plugins/gaim_set_friendly.pl
perl: Loading perl script
perl: Perl function Gaim::Script::gaim_set_friendly::plugin_load exited abnormally: connections is not a valid Gaim::DebugLevel macro at (eval 2) line 49

```

I'm using gaim 2.0.0 beta 3.1

here is a discussion about the plugin, [windlicht]("http://64.233.183.104/search?q=cache:fG-Mn2YjBNAJ:zulutango.org:82/journal/entry/202+gaim+msn+friendly+name+changer&hl=en&ct=clnk&cd=3&client=opera")

---

### Post by jake3988 on 2007-01-14
I enabled it and everything appeared to be going well, but as soon as I enabled it for my account... gaim crashed.  Now it won't start.

Any clues as to how to fix or remove for the time being without messing anything up?


Edit: Ok.  I killed X and all is well.  Any clues as to why pressing the toggle of 'auto-away' in the Accounts menu would crash gaim?

I'm running beta3.1 So I don't think this should be one where it doesn't work.

This is the trace I get after it crashed:
```

*** glibc detected *** gaim: corrupted double-linked list: 0x0863a388 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75a677e]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb75a6a44]
/usr/lib/libcairo.so.2[0xb7949882]
/usr/lib/libcairo.so.2(cairo_new_path+0x1d)[0xb793f49d]
/usr/lib/libcairo.so.2(cairo_clip+0x1a)[0xb793fd2a]
/usr/lib/libgdk-x11-2.0.so.0(_gdk_gc_update_context+0x1eb)[0xb7a2772b]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a2be46]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a2c407]
/usr/lib/libpango-1.0.so.0(pango_renderer_draw_glyphs+0x65)[0xb79b96a5]
/usr/lib/libpango-1.0.so.0(pango_renderer_draw_layout_line+0x44c)[0xb79b9b2c]
/usr/lib/libpango-1.0.so.0(pango_renderer_draw_layout+0x10a)[0xb79b9e9a]
/usr/lib/libgdk-x11-2.0.so.0(gdk_draw_layout_with_colors+0x376)[0xb7a2b3f6]
/usr/lib/libgdk-x11-2.0.so.0(gdk_draw_layout+0x105)[0xb7a2b5d5]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c3fdf0]
/usr/lib/libgtk-x11-2.0.so.0(gtk_paint_layout+0xb9)[0xb7c3c2b9]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b0de4a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_cell_renderer_render+0x94)[0xb7b067e4]
/usr/lib/libgtk-x11-2.0.so.0[0xb7cd0afd]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_tree_view_column_cell_render+0xa9)[0xb7cd1859]
/usr/lib/libgtk-x11-2.0.so.0[0xb7ccadf0]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7bccb00]
/usr/lib/libgobject-2.0.so.0[0xb7904fb9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb790679b]
/usr/lib/libgobject-2.0.so.0[0xb79171e3]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb7917e7f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7918279]
/usr/lib/libgtk-x11-2.0.so.0[0xb7ce05f8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x534)[0xb7bc7314]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a3ad5f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0x97)[0xb7a3afa7]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b37872]
/usr/lib/libglib-2.0.so.0[0xb7890aa1]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7892802]
/usr/lib/libglib-2.0.so.0[0xb78957df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7895b89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7bc7574]
gaim(main+0x88c)[0x810fd0c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75558cc]
gaim(gtk_widget_grab_focus+0x3d)[0x806ed21]

```

---

### Post by tommyvyo on 2007-01-25
This same thing happens to me... clicking enable auto-profile or auto-away will crash gAIM... It was working fine up till a few weeks ago.

---

### Post by jake3988 on 2007-01-26
Well.  Oddly enough, after pressing the 'auto away' for my account and having gaim crash 5 or 6 times, it finally stuck once.

Usually after I restart gaim, the auto-away would switch back to 'off'.  But one time it stayed on 'on' and it works perfectly now.

---

### Post by kapetanski on 2007-01-26
But as I mentioned before, have anyone of you actually seen it working from another msn account? It works in gaim, but your friends does not see it.

---

### Post by jake3988 on 2007-01-26
It claims it sets it as an away, but I'm fairly certain it sets it as an 'available' message.  Things like aol (not aim) do not have support for such messages.

Maybe msn is the same way?

---

### Post by tommyvyo on 2007-01-27
Maybe there is a config file we can edit to turn it on manually?

---

### Post by tommyvyo on 2007-01-27
Maybe there is a config file we can edit to turn it on manually?

Edit: Sorry, I lagged out.. didn't mean for the double post.

---

### Post by lavid on 2007-02-26
Hey, I found a different program/plugin that works for XMMS, amarok, exale, and audacious. It doesn't work too well for any songs with accents or whatnot but it works with the GAIM from svn as of this post.

[http://code.google.com/p/musictracker/](http://code.google.com/p/musictracker/)

---

### Post by KSDZ on 2007-03-16
Hej, I improved the script found earlier in this thread.
It now resets the name as you pause/stop the music, and sets it again when you hit play.

here it is:
```

#!/usr/bin/python
# -*- coding: UTF-8 -*-

# gaim-rb.py
# Update gaim messages and friendly names with information for currently playing song.
# Originally written by: Unknown
# Improved by Koen Sadza <koen@sadza.nl> - http://weblog.ksdz.nl

import dbus
import dbus.glib
import gtk

#class IMAccount: # empty class to put account variales into
#    pass

bus = dbus.SessionBus()
rbshellobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Shell')
rbshell = dbus.Interface(rbshellobj, 'org.gnome.Rhythmbox.Shell')
rbplayerobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')
rbplayer = dbus.Interface(rbplayerobj, 'org.gnome.Rhythmbox.Player')
gaimobj = bus.get_object('net.sf.gaim.GaimService', '/net/sf/gaim/GaimObject')
gaim = dbus.Interface(gaimobj, 'net.sf.gaim.GaimInterface')

value = ''

def update_gaim(value):
    accounts = gaim.GaimAccountsGetAllActive()
    for account in accounts:
#        print account
        protocol = gaim.GaimAccountGetProtocolId(account)
#        print protocol
        status = gaim.GaimAccountGetActiveStatus(account)
        status_id = gaim.GaimStatusTypeGetId(gaim.GaimStatusGetType(gaim.GaimAccountGetActiveStatus(account)))
        if (protocol == 'prpl-oscar') | (protocol == 'prpl-jabber'): # set the away message for oscar and jabber
            message = gaim.GaimStatusGetAttrString(status, 'message')
#            print message
            if message.find(" &#9834;") != -1:
                message = message[:message.find(" &#9834;")]

            gaim.GaimStatusSetAttrString(status, 'message', message + value)
            message = gaim.GaimStatusGetAttrString(status, 'message')
#            print message
        elif protocol == 'prpl-msn': # set the friendly name for msn
            connection = gaim.GaimAccountGetConnection(account)
            message = gaim.GaimConnectionGetDisplayName(connection)
#            print message
            if message.find(" &#9834;") != -1:
                message = message[:message.find(" &#9834;")]

            gaim.GaimConnectionSetDisplayName(connection, message + value)
            
def playing_uri_changed(uri):
    global value
    props = rbshell.getSongProperties(uri)
    value = ' &#9834; \"' + props['title'] + '\" by ' + props['artist'] + ' &#9834;'
#    print value
    update_gaim(value)
    
def playing_changed(truefalse):
    if truefalse:
        update_gaim(value)
    else:
        update_gaim('')
        
rbplayer.connect_to_signal('playingUriChanged', playing_uri_changed)
rbplayer.connect_to_signal('playingChanged', playing_changed)

gtk.main()

```

BTW: Does anybody know if this can be released under GPL? Because the original writer is unknown and I already posted it here? I really don't understand all that licensing stuff...

Edit: I just found out that the Jabber and ICQ status aren't being updated,
this looks like it's due to a bug in Gaim as the dbus GaimStatusGetAttrString returns exactly what GaimStatusSetAttrString set,
but the status isn't being updated in Gaim itself...
If anybody knows how to fix this... Your help is more than welcome.

---

### Post by fornix on 2007-03-22
Cool. I found what i was looking for. A plugin for gaim which changes status to the currently playing song in amarok, xmms, exaile,audicious. 

[http://code.google.com/p/musictracker/]("http://code.google.com/p/musictracker/")

Its called musictracker and it even changes the Nick of Msn to the currently playing song to make for the old msn protocols used by gaim.
Works smoothly here.

---

### Post by neomi on 2007-03-24
so how can I see my contact's now playing info?

---

### Post by kwaanens on 2007-04-02
> ./configure seems to work OK.
But:

$ make
make: *** No targets specified and no makefile found.  Stop.

Using Gaim 2.0.0 beta 6 from debuntu

Nevermind. Missing libgtk-dev headers of course...

- K

---

### Post by pneedleman on 2007-04-07
try putting it in /usr/lib/gaim

---

### Post by arisuke on 2007-06-26
> **kwaanens said:**
> Nevermind. Missing libgtk-dev headers of course...

- K

I got same problem while install musictracker, and i've install libgtk-dev but this not solve my problem. :( Any other way?

---

