---
title: "HOWTO: Snippits for desktop-wide text replacement power!"
date: 2008-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by peabody on 2008-01-27
Snippits is a text expansion ruby program for Linux like Texter and Textpander.  This howto describes how to get it up and running on Ubuntu gutsy.

**1) install necessary packages**

```

sudo apt-get install ruby ruby1.8-dev rdoc rubygems libruby-extras xautomation xsel aspell libaspell-dev aspell-en build-essential
sudo gem install raspell
sudo gem install snippits

```

**update: thanks to the raven for pointing out that raspell has some additional dependencies**

**2) modify your path.  NOTE: according to the lifehacker article, it looks as though this step may not be necessary.  who knows, try it both ways.**

Once those are done, you need to add the gems bin folder to your path.  Put the following line at the end of your ~/.profile.

```

export PATH="/var/lib/gems/1.8/bin:$PATH"

```

**3) logout and login**

You'll want to logout and log back in for the changes to your path to take effect.

**4) Create your snippits folder**

Create a folder called ~/.snippits

```

mkdir ~/.snippets

```

**Confirm everything is working**

You now have everything you need to run snippits.  Make a file called test in the ~/.snippits folder.

```

gedit ~/.snippits/test

```

Type any sort of text you want in there, save and close.  Now open gedit again.  Now we're really going to make sure everything is in place.  With gedit in front of you, do the following:

[LIST=1]
[*]Press Alt+F2 to pull up the Run Command... dialog box
[*]Type 'ks test' and hit enter
[/LIST]

What you typed in the the ~/.snippits/test file should get typed into gedit.

**Time to make things smooth...**

Now that snippits is working, we want to make it easy to use:

**5) Create a {paste} snippit**

```

gedit ~/.snippits/do

```

Put the following into the file:

```

{shift}{control}{left}{shift}c{control}{paste}

```

Save and close the file

**6) Map a keyboard shortcut to 'ks do'**

There are several ways to do this and it's too hard for me to describe them all.  I'll cover the compiz way for now.

Install compizconfig-settings-manager

```

sudo apt-get install compizconfig-settings-manager

```

Go to System -> Preferences -> Advanced Desktop Effect Settings

You should see something that looks similar to below:


[[img]http://img518.imageshack.us/img518/7636/screenshotcompizconfigspw5.th.png[/img]](http://img518.imageshack.us/my.php?image=screenshotcompizconfigspw5.png)

Click on General Settings and then the commands tab.

Type in

```

ks do

```

to command 0, then click on the actions tab and click the arrow next to the commands line item.  Click on run command 0, and press a shortcut key (I used f6).

Close Advanced Desktop Effect Settings.

**7) Test this setup**

Create another snippit, we'll call this one test2

```

gedit ~/.snippits/test2

```

Put something in here, save it, and close.

Open up gedit again, type test2 and hit your shortcut key (f6 in my case).

If everything has gone according to plan, the text should automatically be highlighted, copied to the clipboard, and then the snippit called test2 will be expanded.

Now all you need to do to have a shortcut that can be expanded is to name a single word file (like email) in your ~/.snippits folder.  Put your email address in there.  Now you can type email<f6> in just about any X program that supports the copy operation with ctrl+c to have your email address quickly expanded.

Good luck, and happy texting.

---

### Post by therevan on 2008-01-31
Thank you very much for the instructive walk-through, peabody!

Quick question though: Having a lot of trouble with installing raspell, which in turn seems to make it hard for snippits to install. Here's the code return from running "sudo gem install raspell" . Any advice?

```
Building native extensions.  This could take a while...
ERROR:  While executing gem ... (Gem::Installer::ExtensionBuildError)
    ERROR: Failed to build gem native extension.

ruby extconf.rb install raspell
checking for ruby.h... yes
checking for aspell.h... no
checking for main() in -laspell... no
creating Makefile

make
cc -I. -I. -I/usr/lib/ruby/1.8/i486-linux -I. -DHAVE_RUBY_H  -fPIC -fno-strict-aliasing -g -O2  -fPIC  -c raspell.c
In file included from raspell.c:2:
raspell.h:6:20: error: aspell.h: No such file or directory
raspell.c:13: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
...
```

---

### Post by therevan on 2008-01-31
I found my solution! Turns out raspell requires a few more dependencies to get installed.

Pulling from this link: [http://blog.evanweaver.com/files/doc/fauna/raspell/files/README.html]("http://blog.evanweaver.com/files/doc/fauna/raspell/files/README.html"):

```
sudo apt-get install aspell libaspell-dev aspell-en
```

---

### Post by peabody on 2008-01-31
Ah, thanks theraven, looks like I already had aspell installed...didn't realize it wasn't installed per default in Ubuntu.  I'll see if I can update the guide.

---

### Post by db0 on 2008-02-08
Hello, I'm trying to make this work but is just not accepted in my PATH.

I run the export command, logout, log back in and ks still does not run by default

I tried to just go to a terminal (Alt-F1) and do the export command and logoff/logon, but still the same.

Any ideas?

---

### Post by peabody on 2008-02-10
Two things are possible.  One...you aren't using bash as your shell, or Two...you have a ~/.bash_profile file.  If you have one of those, put the path statement in there.  Make sure it's at the bottom of the file.

[edit]

It also couldn't hurt to make sure that /var/lib/gems/1.8/bin is an actual folder.  If it's not, something went wrong during the installation.

---

### Post by db0 on 2008-02-11
Alright, I put it in my .bash_profile file (without the export) and it seemed to work on the terminal login. I'm going to try and logoff now. I would have tried that sooner but I was not certain why having the path statement in your bash profile would help for the DE :-/

EDIT: Works! Great! Thanks! :)

PS: [Lifehacker]("http://lifehacker.com/351285/automate-repetitive-typing-with-snippits") has an article on it which should be useful for some starting macros ;)

---

### Post by db0 on 2008-02-11
I'm trying to make the script paste the content of either the clipboard or X clipboad as part of the script but unfortunately I can't get it to do it as part of the process is copying your the script into the clipboard.

For example, I want to copy a url in firefox and put it within a bbcode link

I tried the script like so
```

[.url={c}v{c}]{cursor}[/url.]

```
(without the dots in the url bbcode of course)

But it pastes nothing in the url link position

Any idea? I was trying to use the X-Windows clipboard and paste with a middle click but apparent keyout does not accept mouse click option (or so it seems) Any idea? Do you know of any way to paste the contents of the X-Clipboard instead of middle-clicking?

---

### Post by peabody on 2008-02-11
Wow, cool, glad to see lifehacker gave it attention, I know they're big text replacement tool fans.

It looks like build-essential should be installed to have raspell install correctly, I'll update the guide.

The clipboard thing's a definite problem.  I hope Ben gets around to figuring out how to replace while you type (that's what my autokey program does, but my program's a buggy mess :D, his is much cleaner).  Only thing I can think of is if there's a way to drive a program such as Glipper with keyboard shortcuts so that you can get it to change the contents of the clipboard.

---

### Post by db0 on 2008-02-11
> **peabody said:**
> 
The clipboard thing's a definite problem.  I hope Ben gets around to figuring out how to replace while you type (that's what my autokey program does, but my program's a buggy mess :D, his is much cleaner).  

Yah, mee too. For now I can still use to to paste nifty stuff for wesnoth  scenario scripting ;)

> Only thing I can think of is if there's a way to drive a program such as Glipper with keyboard shortcuts so that you can get it to change the contents of the clipboard.

I checked Glipper and unfortunately it does not have an option to change the shortcuts. It would be cool if it supported something like ctrl+1 to paste the first entry in Glipper, ctrl+2 for the second and so on :-/

At least an option to change the shortcut for the selection clipboard instead of middle mouse click.

---

### Post by peabody on 2008-02-11
best I can come up with in using glipper

```

[.url={cursor}][/url.]

```

that'll leave cursor where you want it.  Then use Ctrl+Alt+c, navigate with the arrow keys to pick the clipboard text you want from glipper, hit enter, and hit Ctrl+v.  Not nearly so nice as automatically wrapping the clipboard, but better than nothing.

If you really, really, reeeeally want something like that, you can try braving my program (it's in my sig).  It works well enough for me, but I can guarantee that if you have any sort of international keyboard (read: something outside the US) it probably won't work.  My program does automatically replace text as you type, and can call shell programs (I have an example in the abbr.ini file of using the xclip program to paste out the clipboard).

---

### Post by db0 on 2008-02-11
Ok, my best one is this
```

[.url={c}{a}c{a}{c}{sleep}{down}{down}{enter}{sleep}{c}v{c}]{cursor}[/url.]

```

You need the sleep functions because otherwise it executes faster that glipper can open ;)

This seems to work but it may delay you 2 seconds

I dare you to outdo me :P

---

### Post by peabody on 2008-02-11
> **db0 said:**
> 
I dare you to outdo me :P

HA!  Okay, how about this...it requires the xclip program, but I think it's a pretty cool hack if I do say so myself.

change your 'do' snippit to this:

[Edit: removed an unnecessary {sleep}]

```

<%`xclip -o -selection clipboard | xclip -i -selection secondary`%>{shift}{control}{left}{shift}c{control}{paste}

```

those are grave accent marks not quotes, so be careful when copying them...

Now, if you have have a snippit in which you want to paste the clipboard, do this:

```

[.url=<%= `xclip -o -selection secondary` %>][/url.]

```

This is basically exploiting the secondary clipboard meant for just this kind of thing.  xclip is taking the contents of the clipboard and copying it to the secondary clipboard.  Then, if it's needed, you  can paste from it in your snippits.

This exploits the fact you can run embedded ruby code in your snippits.  I'm basically running shell commands and in ruby and printing the output.

---

### Post by db0 on 2008-02-11
/me outdone :(

Snippits does become a bit slower (*see PS) with this workaround so I created a do2 option which I've mapped to a different shortcut for this purpose. My original was pause and the xclip one is shift+pause. 

Well done :)

PS: I removed the sleep of your function and it still works normally (and at normal speed). Did you put the {sleep} there for a specific reason? Will it break anything I don't expect if I remove it?

---

### Post by peabody on 2008-02-11
Nope, won't break a thing, I'm not sure why it was in there in the first place, I've since removed it.

---

### Post by db0 on 2008-02-11
In any case, I'm glad I challenged you ;)

---

### Post by db0 on 2008-02-11
[blogged](http://www.dbzer0.com/blog/2008/02/11/improving-snippits-to-handle-the-clipboard) and [Screencasted](http://www.youtube.com/watch?v=3hThXfzyKvE)

I used instanbul to do it and the text is a bit distorted. Is this the same program you used for your own screencast?

---

### Post by peabody on 2008-02-11
I used recordmydesktop, with gtk-recordMyDesktop as a frontend.  And of course, the compiz enhanced zoom desktop (window key + scroll wheel).

---

### Post by Tetsujin-28 on 2008-02-15
I've been using snippits as a text expander in Kubuntu for a few months now, and it's been very useful. However, I've been configuring a completely different hotkey combo for each snippit. The idea of using the single "do" snippit looks so much more elegant -- but I can't get it to work!

I know that my snippits work. For example, I have a snippit file named "test" that contains "This is a test snippit."  When I'm in a text editor and use alt-f2 to execute "ks test" I get "This is a test snippit."

However, if I type "test" and then execute "ks do" (via a hotkey or alt-f2), all that happens is that "test" is highlighted and copied to my clipboard. "ks test" is never executed, and no text is replaced.

My "do" snippit reads:

```
{shift}{control}{left}{shift}c{control}{paste}
```

Any suggestions? Maybe something is wrong with my "do" snippit, or my configuration?

Thanks --T.

---

### Post by peabody on 2008-02-15
Only thing I can think of is to insert some {sleep} commands in there.  Maybe it isn't getting copied to the clipboard fast enough for the {paste}?

---

### Post by Tetsujin-28 on 2008-02-15
I've done more testing and it seems that {paste} just isn't working for me. Time to do some digging around...

---

### Post by peabody on 2008-02-16
do you have either the xsel or xclip packages installed?  I think one or the other is required for paste to work.

---

### Post by db0 on 2008-02-16
Another thing to try is to close the ctrl before copying and then opening it again before "pressing" the button and instead of c (copy) use x (cut). 

```
{c}{s}{left}{c}{s}{c}x{c}{paste}
```

---

### Post by Tetsujin-28 on 2008-02-16
That was it -- I didn't have xsel installed. All is good now. Thanks!

---

### Post by eamonireland on 2008-05-02
I've tried to get snippits to work since I switch to Ubuntu. I can never do it, so I leave it for a while, when hopefully my knowledge has improved.

I tried again today, but I can't even get 'ks test' to work. I get this message

Could not open location 'file:///home/eamon/ks%20test'

Why does everything have to be so complicated??

---

### Post by DamonChyld on 2008-05-02
```
~$ snippit test
bash: snippit: command not found
```
```
 ALT-F2, ks test = Could not open location 'file:///ks test'
```
I can not seem to get the program to run. I have followed the instructions on the [lifehacker]("http://lifehacker.com/351285/automate-repetitive-typing-with-snippits") page, [project]("http://ben.kudria.net/code/snippits") homepage, and here but am getting no joy. The only step that I did not do from any of these sites was step 2 of Peabody's walk-thru; I do not have a ~/.profile folder.

dependencies:
```
~$ sudo apt-get install ruby ruby1.8-dev rdoc rubygems libruby-extras xautomation xsel aspell libaspell-dev aspell-en build-essential
[sudo] password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ruby is already the newest version.
ruby1.8-dev is already the newest version.
rdoc is already the newest version.
rubygems is already the newest version.
libruby-extras is already the newest version.
xautomation is already the newest version.
xsel is already the newest version.
aspell is already the newest version.
libaspell-dev is already the newest version.
aspell-en is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and the program:
```
~$ sudo gem install snippits
Successfully installed snippits-0.5.2
Installing ri documentation for snippits-0.5.2...
Installing RDoc documentation for snippits-0.5.2...

```(Program installed without any errors the first time I ran it, installs ri documentation and RDoc documentation every time)

Does anyone have an idea as to what I am doing wrong, I can not wait to get this program working!

---

### Post by peabody on 2008-05-03
try this in a shell:

```

locate 'bin*snippit'
echo $SHELL
echo $PATH
ls ~/.profile ~/.bash_profile ~/.login

```

Copy and paste the output here and I may be able to help.

---

### Post by therevan on 2008-05-03
Hey all:

I'm the author of the previously-cited [_Lifehacker post on Snippits_]("http://lifehacker.com/351285/automate-repetitive-typing-with-snippits"), and I'm looking to update the post for Hardy Heron installations -- mostly because I myself couldn't get Snippits working, at least not on a first try using my old instructions.

I'm thinking part of it has to do with new packages/dependencies. The basic operation and use of system resources/calls remains the same, I'd assume. Anybody have *any* luck installing and working in Hardy?

---

### Post by peabody on 2008-05-04
If I have the time I'll do a virtual box install of Hardy to test out sometime next weekend.

---

### Post by StrangeFreedom on 2008-05-04
This is what I get on hardy:

$ ks do
```
/var/lib/gems/1.8/gems/snippits-0.5.2/lib/typing.rb:171: Interrupt
	from /var/lib/gems/1.8/gems/snippits-0.5.2/lib/typing.rb:299:in `call'
	from /var/lib/gems/1.8/gems/snippits-0.5.2/lib/typing.rb:299:in `type_text'
	from /usr/lib/ruby/1.8/erb.rb:743:in `each_with_index'
	from /var/lib/gems/1.8/gems/snippits-0.5.2/lib/typing.rb:294:in `each'
	from /var/lib/gems/1.8/gems/snippits-0.5.2/lib/typing.rb:294:in `each_with_index'
	from /var/lib/gems/1.8/gems/snippits-0.5.2/lib/typing.rb:294:in `type_text'
	from /var/lib/gems/1.8/gems/snippits-0.5.2/bin/ks:17
	from /var/lib/gems/1.8/bin/ks:16:in `load'
	from /var/lib/gems/1.8/bin/ks:16
```

---

### Post by peabody on 2008-05-07
I just did a Virtual Box install of Hardy and had zero trouble getting snippits working so I'm not sure what the problem is.  Only thing I can recommend is to try to reinstall the snippits gem:

```

sudo gem uninstall snippits
sudo gem install snippits

```

If you upgraded to hardy it could be the old gem install doesn't work under the new libraries.

---

### Post by aboutblank on 2008-05-08
I'm on Hardy and this is how I got Snippits to work for me.

* Skipped step 5 in the OP (I did not create the paste 'do' script)
* In step 6, bind to 'ks keyword' as stated in the [instructions]("http://snippits.rubyforge.org/")

I don't believe the creator intended for the 'do' script the OP creates. My installation works as just typing a script name like 'name' and pressing the hotkey. 

Good luck!

---

### Post by db0 on 2008-05-31
Hmm, I now have another problem. I installed snippits on my girlfriend's laptop which has as the default keyboard a german layout (qwertz). I've set it up to use the normal international (qwerty) for my own profile.

Now the weird part is that snippits, instead of writing the character I've set up, seems to put the character of the systems default layout at that position.

Thus, for example, my emails address from [email]mail@dbzer0.com[/email] becomes mail dbyer0.com (including the space) as the @ and z are at different locations.

Any idea how to fix this?

---

### Post by iforwms on 2008-08-09
> **DamonChyld said:**
> ```
~$ snippit test
bash: snippit: command not found
```
```
 ALT-F2, ks test = Could not open location 'file:///ks test'
```
I can not seem to get the program to run. I have followed the instructions on the [lifehacker]("http://lifehacker.com/351285/automate-repetitive-typing-with-snippits") page, [project]("http://ben.kudria.net/code/snippits") homepage, and here but am getting no joy. The only step that I did not do from any of these sites was step 2 of Peabody's walk-thru; I do not have a ~/.profile folder.

dependencies:
```
~$ sudo apt-get install ruby ruby1.8-dev rdoc rubygems libruby-extras xautomation xsel aspell libaspell-dev aspell-en build-essential
[sudo] password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ruby is already the newest version.
ruby1.8-dev is already the newest version.
rdoc is already the newest version.
rubygems is already the newest version.
libruby-extras is already the newest version.
xautomation is already the newest version.
xsel is already the newest version.
aspell is already the newest version.
libaspell-dev is already the newest version.
aspell-en is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and the program:
```
~$ sudo gem install snippits
Successfully installed snippits-0.5.2
Installing ri documentation for snippits-0.5.2...
Installing RDoc documentation for snippits-0.5.2...

```(Program installed without any errors the first time I ran it, installs ri documentation and RDoc documentation every time)

Does anyone have an idea as to what I am doing wrong, I can not wait to get this program working!

This is driving me mad, spent hours trying to sort this now! Same problem as above!

When I open a terminal and run ks test is types the text before AND after the terminal prompt, but I get the same error as quoted poster when I try and run it using Alt+F2. Did not have a .bashrc or .bash_profile in my Home folder for some reason, but created them using default template and made them executable but still no luck.

Any help would be greatly appreciated!

Inserted symlinks of the contents of the gems/1.8 folder into /urs/bin/ and all seems to work. think its a problem with my .bashrc files...

---

### Post by BionicSeahorse on 2008-09-01
I finally got it to work in Hardy amd64!

Steps:
[LIST=1]
[*]add the following to your ~/.bashrc:```
export RUBYOPT="rubygems"
export PATH=$PATH:/var/lib/gems/1.8/bin

```
[*]run the following command inside the terminal: ```
source ~/.bashrc
```
[*]log off/on
[*]install gizmod (in the repos) by running ```
sudo aptitude install gizmod
```
[*]Modify the **199-Keyboard-Default.py** script to catch your Snippits hotkey (KEY_PAUSE in my case) [ [The script is here]("http://pastebin.com/f35975322") ]
[*]run gizmod
[/LIST]

Basically, what I did was to bypass Compiz for the hotkeys. I also didn't need to create a "do" script as in the OP from Lifehacker. Gizmod saves the day once again!

BTW, this works on both the terminal and GDM. :guitar:

---

### Post by azulmarino on 2008-10-14
Snippits works well for me except for the following issues:

Note: my keyboard layout is Latin American.

1 - The """ character (double quotes) in a snippit gets copied as "?"
2 - The "<" character in a snippit gets copied as ";"
3 - Using the xclip enabled do snippit, if the clipboard contains any accented character like in "Café", this character is missing from the replacement output.
4 - Any accented character (like "é") in a snippit is missing from the replacement output.

The first two issues prevent me from programming snippits for HTML tag replacement.

The last two issues prevent me from programming a snippit to output my name.

Any helpful ideas will be welcome :)

---

### Post by Fabiano Shark on 2008-10-15
**[COLOR="Red"] ALT-F2, ks test = Could not open location 'file:///ks test'[/COLOR]**

> **iforwms said:**
> This is driving me mad, spent hours trying to sort this now! Same problem as above!

When I open a terminal and run ks test is types the text before AND after the terminal prompt, but I get the same error as quoted poster when I try and run it using Alt+F2. Did not have a .bashrc or .bash_profile in my Home folder for some reason, but created them using default template and made them executable but still no luck.

Any help would be greatly appreciated!

Inserted symlinks of the contents of the gems/1.8 folder into /urs/bin/ and all seems to work. think its a problem with my .bashrc files...

Try to paste this in the end of your ~/.bashrc:
```
 PATH="/var/lib/gems/1.8/bin:$PATH" 
```

then run:
```
source ~/.bashrc
```

login/logout and it will probably works ;)


In time, congratulations to the author for this wonderful stuff. =D>

Best regards.,
Fabiano Shark

---

### Post by Fabiano Shark on 2008-10-15
> **therevan said:**
> 
...
**Time to make things smooth...**

Now that snippits is working, we want to make it easy to use:

**5) Create a {paste} snippit**

```

gedit ~/.snippits/do

```

Put the following into the file:

```

{shift}{control}{left}{shift}c{control}{paste}

```

Save and close the file

**6) Map a keyboard shortcut to 'ks do'**

There are several ways to do this and it's too hard for me to describe them all.  I'll cover the compiz way for now.



I'm using **xbindkeys** for shortcut:
[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560) ;)

---

### Post by db0 on 2008-12-28
:(

Anyone have any idea how to work around the foreign character replacement issue?

---

### Post by poisoneggs on 2009-02-12
Snippits is working fine for me, except that the " character changes to an @ .
Anyone knows how to fix this?
I'm using an UK layout keyboard.

---

### Post by danggrianto on 2009-06-25
hi guys i made some modif to snippits. i hope it will help.
to add text to snippits library we need to open text editor and then type the word and sentences and save it to .snippits folder. or to make it easier you can type
```
echo "text to add"">~/.snippits/text
```
it is simple and then you anly call text with your key.
but that's not it.. to make even more simple i wrote a script to recieve the argument here is the code
```
#!/bin/sh
echo $2>~/.snippits/$1
```
name the script "snip" (or whatever u want"
so you only need to run
```
./snip text "text to change"
```
but those code only applies when you work on root folder only. i mean suppose you work on the terminal in different folder ./snip wont work, it will work if you specified the folder such as:
```
~/snip
```
i made some fancy thing. i edit my bin folder and put my snip script into bin folder. you need sudo command and then don't forget to change permission.
```
sudo gedit /bin/snip
```
```
#!/bin/sh
echo $2>~/.snippits/$1
```
```
sudo chmod +x /bin/snip
```

thus you can run on any folder with this command
```
snip text "text to change"
```
PS: dont forget "" mark for more than two words

---

### Post by danggrianto on 2009-06-25
i'll try to make a nice GUI when i have a spare time.. or maybe somebody could do it...
thx

---

### Post by BionicSeahorse on 2009-06-25
> **danggrianto said:**
> hi guys i made some modif to snippits. i hope it will help.

@danggrianto Cool! Works like a charm. Thaks for sharing!

---

### Post by danggrianto on 2009-06-26
no problem man.. this is the way of open source should work.. helping each other rite?

---

### Post by BionicSeahorse on 2009-06-27
Here's a way to use a dialog for creating new snippits on the fly using kdialog (and optionally xbindkeys):

1) Create a new file inside your ~/bin folder called 'snipthis' and paste the following code:
```
#!/bin/sh
snip=`kdialog --title "Create New Snippit [1/2]" --inputbox "What is the shortcut's name?"`
if [ $? -ne 0 ]
then
  echo "Snippit creation cancelled"
  exit 1
fi

text=`kdialog --title "Create New Snippit [2/2]" --inputbox "What is the text that you want to replace the shortcut with?" "This is some dummy text"`
if [ $? -ne 0 ]
then
  echo "Snippit creation cancelled"
  exit 2
fi

echo $text>~/.snippits/$snip
echo "Snippit $snip has been created successfully!"
```

2) Make it executable:
```
chmod +x ~/bin/snipthis
```

3) Type 'snipthis' on the command line and fill in the blanks. You're done!

4) For extra points, install xbindkeys and add this to your ~/.xbindkeysrc file:
```
#Create new snippit
"snipthis"
    m:0x14 + c:96
    Control + F12
```

Now every time you press Ctrl+F12 you can create a new snippit on the fly!
Hope that helps someone out. Props to danggrianto for the inspiration :)

---

### Post by light50 on 2009-06-27
Hi, thanks for this great thread. I have used it many times as I can't do without this functionality. Of note however on an Intrepid machine I recently encountered a problem with rubygems:
```
$ sudo gem install snippits
```
gave me:
```
hoe requires RubyGems version >= 1.3.1
```
I found a solution [[COLOR="RoyalBlue"]here[/COLOR]]("http://intertwingly.net/blog/2008/11/23/RubyGems-1-3-1-on-Ubuntu-8-10"), which was basically:
```
$wget http://rubyforge.org/frs/download.php/45905/rubygems-1.3.1.tgz
$ tar xzf rubygems-1.3.1.tgz
$ cd rubygems-1.3.1
$ sudo ruby setup.rb
```

---

### Post by light50 on 2009-06-27
Ah just noticed this:

> **BionicSeahorse said:**
> 
```
#!/bin/sh
snip=`kdialog --title "Create New Snippit [1/2]" --inputbox "What is the shortcut's name?"`
if [ $? -ne 0 ]
then
  echo "Snippit creation cancelled"
  exit 1
fi

text=`kdialog --title "Create New Snippit [2/2]" --inputbox "What is the text that you want to replace the shortcut with?" "This is some dummy text"`
if [ $? -ne 0 ]
then
  echo "Snippit creation cancelled"
  exit 2
fi

echo $text>~/.snippits/$snip
echo "Snippit $snip has been created successfully!"
```

Nice one. Here's a Gnome version using Zenity:

```
#!/bin/sh
snip=`zenity --entry --title="Enter name" --text="What is the shortcut's name?"`
if [ $? -ne 0 ]
then
  zenity --info --title="Cancelled" --text="Snippit cancelled"
  exit 1
fi

text=`zenity --entry --title="Enter text" --text="What is the text that you want to replace the shortcut with?"`
if [ $? -ne 0 ]
then
  zenity --info --title="Cancelled" --text="Snippit cancelled"
  exit 2
fi

echo $text>~/.snippits/$snip
zenity --info --title="Done" --text="Snippit $snip has been created successfully!"
```

---

### Post by light50 on 2009-06-27
Here's another one that takes text from the primary clipboard:
```
#!/bin/sh
text=`xsel -p`
snip=`zenity --entry --title="Enter name" --text="What is the shortcut's name?"`
if [ $? -ne 0 ]
then
  zenity --info --title="Cancelled" --text="Snippit cancelled"
  exit 1
fi

echo $text>~/.snippits/$snip
zenity --info --title="Done" --text="Snippit $snip has been created successfully!"
```
or to add a notification popup, replace the last line with:
```
notify-send ["snippits"] "The snippit $snip has been created"
```

---

### Post by dt_matthews on 2010-09-06
> **peabody said:**
> Ah, thanks theraven, looks like I already had aspell installed...didn't realize it wasn't installed per default in Ubuntu.  I'll see if I can update the guide.

hi peabody,

I wonder if you can advise me, I have installed snippits with dependencies and it all installed ok. I can run a snippit explicitly (ks name) for example. I cannot however get the key-binding section to run the do script. I am running lucid and when I use keyboard shortcuts and assign 'ks do' to a key (e.g. F3) I just get the error;

"Error while trying to run (ks do)
which is linked to the key (F3)"

I'd really appreciate ANY pointers as I dont really no where to try and diagnose and correct the problem!

TIA,
dan

---

