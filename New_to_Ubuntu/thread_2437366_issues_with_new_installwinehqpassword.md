---
title: "issues with new install/winehq/password"
date: 2020-02-22
forum: New to Ubuntu
---

### Post by hogdigerdy on 2020-02-22
hi everyone new to Ubuntu, just about ready to pull me eyeballs out
downloaded 18.04 bionic to disc, went for clean install with no issues downloaded wine and winetricks without any issues except esetnod32 would not open, tried the 32 and 64 bit downloads neither worked,so went back to the beginning and uninstalled wine and winetriks
then found winehq and am stuck trying to use command prompt/ /terminal to reinstall although i used these yesterday 
the problem is the password terminal/cp is asking for, 
i am using the word i use to sign into Ubuntu but terminal/cp will not accept it
any help would be much appreciated

---

### Post by deadflowr on 2020-02-22
What do you mean not accept?
Is it saying wrong or incorrect password, or something else?

---

### Post by hogdigerdy on 2020-02-22
[sudo[ password for steve 
then i cant type anything after that unless i copy and paste
i am trying to copy in the 32bit architecture 
sudo dpkg --add-architecture i386
then it says
[sudo[ password for steve 
and i can't enter a password 
i made it passed this point once and password was not accepted, can't remember exactly what it said

---

### Post by deadflowr on 2020-02-22
The password field is blank and invisible, so you need to type it as best you remember it and hit enter.
(And hope you typed it right)
ftr

---

### Post by hogdigerdy on 2020-02-22
it says

~$ sudo dpkg --add-architecture i386
[sudo] password for steve: 
Sorry, try again.
[sudo] password for steve: 

that's all i keep getting obviously doing some thing dumb

---

### Post by coffeecat on 2020-02-22
If the password you believe you are typing into the terminal is the same as your login password, and your login password is working, then you must be making an error when typing it into the terminal (assuming you are logged into the administrator account). Because you get no visible feedback from the terminal when you type your password, it is easy to make a mistake. We've all done it. Check that you haven't accidentally activated caps lock. 

Here's a way of making sure that you are putting the correct password into the terminal. Open a text editor, and type out your password, and double-check that you have typed it correctly. Highlight the typed password and press crtl-c to copy it into the clipboard buffer. Now, in the terminal, type your sudo command. When the sudo password prompt appears, simply press ctrl-shift-v to paste your password into the terminal. Nothing will appear to happen, but your password has been pasted. Now press enter.

---

### Post by hogdigerdy on 2020-02-22
i have tried this
but have just tried it again and get
'password : command not found'
perplexed

---

### Post by Dennis N on 2020-02-22
Aside from your password problem, you no longer need to add the i386 architecture. 64-bit systems support it by default. Verify with this command:
```
dmn@Sydney-VM:~$ dpkg --print-foreign-architectures
i386

```
You should get i386 as above.

---

### Post by coffeecat on 2020-02-22
> **hogdigerdy said:**
> 
'password : command not found'

The only way I know to get anything like that is to type the word "password" into the terminal. Is that what you did? That's not what you want to do.

Read my suggestion again, and follow it very carefully.

---

### Post by hogdigerdy on 2020-02-22
nope just says command not found
ie
dmn@Sydney-VM:~$: command not found
'my computers name' ~$ i386
hope this helps narrow it down
i read somewhere (winehq site i think) earlier it was only 19 that had it installed, i have 18.04 and need the i386 so i'm told, that's where this whole sorry saga began, i deleted wine and wine tricks to start afresh and have been stuck ever since
the password being the major issue the rest i can probably figure out only have 24hrs on ubuntu

---

### Post by deadflowr on 2020-02-22
You need to cut out the *prompt* that was posted originally
and just run this command
```
dpkg --print-foreign-architectures
```


Edit: To add,
I agree you should re-read coffeecat's [post #6]("https://ubuntuforums.org/showthread.php?t=2437366&p=13934174#post13934174").
Feel free to ask questions about anything you don't understand.

---

### Post by hogdigerdy on 2020-02-22
tried that and got this
$ dpkg --print-foreign-architectures
i386
yes i tried coffeecat's suggestion as i have numerous times but still seem to be getting nowhere
if someone could wright down the code for entering a password it may help
ie
do i include the dollar sign the slashes etc, gaps and so on, some entries have blue highlights then it goes to normal text, do you enter all this or just the normal text
confusion seems to be the name of the game
still havin fun though took ages to get the hang of windows

---

### Post by Holger_Gehrke on 2020-02-22
To go back to your original post, even if you manage to get your problem with sudo and 32-bit libraries sorted out, you probably aren't going to be able to run the program you're trying to run. The Wine App Database has an entry for eset nod32 that says it doesn't even install much less run. Granted, that entry is several years old, but nobody who has tried since has bothered to file a report which makes me think it still won't work. And that makes sense if you take the nature of Windows antivirus programs like nod32 into account. They integrate themselves deeply into the OS to catch (known) malware before it can do any damage and they can't do that on another OS than the one they were written for. There are some anti-malware programs that are meant to run on Linux, but mostly they are meant for disaster recovery from a life boot medium on an infected windows system or for use on file servers that serve Windows clients. Those detect viruses written for Windows. Viruses for Linux are very rare. Which doesn't mean that there are no threats, but they are usually not aimed at desktop users but against servers.

Holger

---

### Post by yancek on 2020-02-22
> [COLOR=#000000]do i include the dollar sign the slashes etc, gaps and so on, some entries have blue highlights then it goes to normal text, do you enter all this or just the normal text[/COLOR] 

When you open a terminal you should see the following 'prompt' if the user is bob:

```
bob@bob-HP-Notebook:~$ 
```

You will see a dollar sign ( $ ) if the terminal is opened as a regular user.  If you are using sudo to get root privileges, the $ will change to # and it is after this where you type in whatever command you want.  You do not add a dollar sign or a hash mark to the beginning of the command.  The slashes are used to indicate the path from one directory to another.  Blue text in a terminal will mean a directory while white is a file, generally.  An example below shows copying a file named network in that  user /home directory to the Downloads directory for that same user and doing it as root, hence the sudo.  You will be able to do this as a normal user in your own directory (/home/user) so don't need sudo.  General rule is that if you want to copy TO a location outside your /home/user directory you need to use sudo.  Any command you run in a terminal is case-sensitive.

```
sudo cp network Download
```

If the above info and example don't help I would suggest you give the Ubuntu Handbook at the link below a thorough read as it seems you are missing some very basic information. 
[URL="https://help.ubuntu.com/"]
https://help.ubuntu.com/[/URL]

---

### Post by hogdigerdy on 2020-02-23
@holger i did speak to eset  technical support and was assure the version i have should work it came from esets ubuntu page  [https://www.eset.com/uk/home/antivirus-for-linux/](https://www.eset.com/uk/home/antivirus-for-linux/) doesn't mean it will work though and as i downloaded a couple other program's and they work i would say you are probably right, ill leave that problem for now

---

### Post by hogdigerdy on 2020-02-23
@yancek that's made things a bit clearer i think i'll re download winehq as an experiment as much as anything and try and get the hang of whatever it is i'm doing wrong, although i appreciate i'll need it anyway, and then do a spot of light reading, your right about my very limited knowledge only had ubuntu almost 48 hrs and only about 10 of them at the keyboard

---

### Post by hogdigerdy on 2020-02-23
@yancek that's made things a bit clearer i think i'll re download winehq as an experiment as much as anything and try and get the hang of whatever it is i'm doing wrong, although i appreciate i'll need it anyway, and then do a spot of light reading, your right about my very limited knowledge only had ubuntu 48 hrs and only about 10 of them at the keyboard

---

### Post by hogdigerdy on 2020-02-23
thanks to everyone that gave input on my issues, i guess i just couldn't see the wood for the tree's, new day, fresh eyes and the terminal is accepting my password have downloaded winehq with no problems,
sometimes it's just better to pack it in and start again refreshed
once again thanks to all

---

### Post by TheFu on 2020-02-23
> **hogdigerdy said:**
> @holger i did speak to eset  technical support and was assure the version i have should work it came from esets ubuntu page  [https://www.eset.com/uk/home/antivirus-for-linux/](https://www.eset.com/uk/home/antivirus-for-linux/) doesn't mean it will work though and as i downloaded a couple other program's and they work i would say you are probably right, ill leave that problem for now

Native Linux apps don't need/cannot use WINE.
I’ve only run an AV on Linux when required to do so by a contract.  It never found anything, ever.

For someone really new to Linux, a quick get acquainted into is needed.  About 80% of Windows knowledge is not useful.
Read this: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)

>  hi everyone new to Ubuntu, just about ready to pull me eyeballs out
through me off.  Were you saying hi only to "everyone new to Ubuntu" or just missing a comma?  Punctuation matters.

---

### Post by hogdigerdy on 2020-02-24
> **TheFu said:**
> For someone really new to Linux, a quick get acquainted into is needed.  About 80% of Windows knowledge is not useful.
Read this: [URL="https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html"]https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html
[/URL]


through me off.  Were you saying hi only to "everyone new to Ubuntu" or just missing a comma?  Punctuation matters.
then punctuation you shall have my good fellow

'hi everyone, new to Ubuntu, just about ready to pull me eyeballs out.'
hope this meets with your approval 

i certainly shall amongst all the other reading I'm doing


onto the eset thing if i downloaded the .exe file from eset for ubuntu (so i don't need wine) why would it not load / execute

---

### Post by TheFu on 2020-02-24
When I downloaded the linux version  of eset, the filename was eset_nod32av_32bit_en_.linux.   
```
$ file eset_nod32av_32bit_en_.linux 
eset_nod32av_32bit_en_.linux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-, for GNU/Linux 2.4.1, stripped
```
that says it is a native Linux 32-bit program.  WINE is not needed - and won't work to run it.  My systems are 64-bit.

After downloading, I changed the permissions to make the file "executable", and ran it.
```
$ chmod +x eset_nod32av_32bit_en_.linux 
$ ./eset_nod32av_32bit_en_.linux 
bash: ./eset_nod32av_32bit_en_.linux: No such file or directory
```
Well, that shouldn't happen.  Found their "quick start guide" and started reading.  They said to modify the permissions like I did, then run it, which I did.  Nothing special in the guide for Ubuntu.  No mention of specific release requirements. Perhaps I don't have a library they think everyone has?  No mention of dependencies in the guide either.

BTW, nobody should see any error for a properly packaged program.

Good thing we don't need this program. Certainly eset is probably a fine program.  The normal AV program on Linux is ClamAV. It is F/LOSS.

Getting a little nerdier, 
```
$ ldd eset_nod32av_32bit_en_.linux 
  not a dynamic executable
```

Ok, time to use some google-fu.  Found this:
[https://support.eset.com/en/kb2653-download-and-install-eset-nod32-antivirus-4-for-linux-desktop](https://support.eset.com/en/kb2653-download-and-install-eset-nod32-antivirus-4-for-linux-desktop)
So there is a 64-bit version.  Let's try that.
```
$ file eset_nod32av_64bit_en.linux 
eset_nod32av_64bit_en.linux: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/l, for GNU/Linux 2.6.0, stripped
$ chmod +x eset_nod32av_64bit_en.linux
$ ./eset_nod32av_64bit_en.linux 
```
That brought up a window telling me to install two libraries that aren't on my system.  libc6:i386 and ld-linux.so.2.  Well, I won't be doing that. Not really interested in running 32-bit software. Sorry.

Anyway, hopefully, seeing me work through this will help you.

---

### Post by Holger_Gehrke on 2020-02-24
If it's an '*.exe' file, then it's not for Ubuntu ... The file I get offered when I go to the link you provided is named eset_nod32av_64bit_de.linux (which would be the 64-bit version with german localization). In Linux the ability to execute a file is not tied to the name or extension, it's one of the permissions stored for the file. The browser for security reasons does not set this permission for downloaded files even if it could tell that it is a program. You can either set the permission through the properties of the file in your file-manager or from the command line using the 'chmod' command ('chmod u+x myfile' would allow the **u**ser owning the file to e**x**ecute 'myfile').

Seen on a postcard recently: "Punctuation saves lives: Let's eat[COLOR=#ff0000],[/COLOR] Grandpa!"

Holger

---

### Post by TheFu on 2020-02-24
Linux doesn't care about file extensions, though they are handy for humans.  A file that has been compiled into a program for the system doesn't need any extension, just the permissions for any users, groups or others need to be eXecute.  They same works for scripts, but those also require "read" permissions for any users, groups or others that should be able to run the script.

Some GUI programs are lazy and do use file extensions, but not all do.  For example, some PDF readers only work with PDF files that are named with the .pdf extension, while other PDF readers only require that the file have a correct PDF header and don't care about the extension.  How this works or doesn't depends on the project developers for the program.  Just another way Unix systems aren't like Windows.

---

### Post by hogdigerdy on 2020-02-25
@holger, by calling it an .exe file i have thrown another spanner in the works, i now realize iv'e been blinded by windows, as any file downloaded that you click on to load a program is generally an .exe file apologies,
i hope gramps ain't to tough

@theFu, yes i'm slowly getting the drift of it, a bit more playing, and if i don't kill the system and need to reinstall, I'll probably get their

---

### Post by TheFu on 2020-02-25
What happens is we assume you said exactly what you meant and that it was the truth.  By saying exe file (which you still haven't said whether that is what you got or not clearly), we took off in a specific directiion and ether wasted a bunch of time on it or explained why WINE wasn't needed.  

See how that might be confusing for us?  We've all been there - well, anyone who used DOS or Windows before using another OS.

At this point, it would be best to copy paste commands here, with any options, show exact filenames, etc. to limit confusion on both sides. I tried to do that in post 21 above.  Those are exact commands.  The leading $ matters - it says, run this as a normal user, not root, not with sudo.   This is normal nomenclature for Unix systems.    Do NOT include it, the $.  It is just there to be clear whether a normal user or elevated privileges are needed.
```
$ = normal user
# = root user
```
They are meant to show the bash prompt.  The default bash prompt on Ubuntu is much more useful.  But that's a completely different thing.  :)

---

### Post by hogdigerdy on 2020-02-28
@ TheFu although i sent you on a wild goose chase your time wasn't totally wasted as i got an idea of the way things should be done, i also gleaned that eset is really not necessary, the reason i wanted to get the eset argument sorted, is my subscription is almost up, as i don't really need it i shan't waste my £20, so your time spent has saved me 20 quid, cheers, 
also i now understand that wine is only for use if you want to run a windows programe, 
still about as green as they come but i'm getting their, reading through old posts and getting to grips with the article you recommended
so thanks to everyone who posted replies once again

---

