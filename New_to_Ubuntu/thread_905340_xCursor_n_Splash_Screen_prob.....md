---
title: "xCursor n Splash Screen prob...."
date: 2008-08-30
forum: New to Ubuntu
---

### Post by yogen on 2008-08-30
heyy guys..i hav encountered an unusual prob(i think so)...

whn I start da splash screen app...n press da install button after browsing for da desired screen...da splash screen program gets terminated ...!!!
i hav tried atleast thousand times...but in vain...!!!

hav refrd sum forums too...but of no use...is sum1 der...!!!

---

### Post by gmxgeek on 2008-08-30
Could you perhaps repost with a little more details, and perhaps a bit better spelling. When posting questions for help on forums, it helps a lot that you go into as much detail as possible, and speak properly so that everyone can understand you. If no one can understand what the problem is, or you are beginto vauge (ZOMG!!!!!1 ITS BR0K4N!!1!!1!!!) then it makes it very difficult for others to help you out.

---

### Post by yogen on 2008-08-30
a'right...sry for that lingo..

my problem is...in splash screen, after i browse and select my desired screen and press the install button...the program terminates...!!!

---

### Post by gmxgeek on 2008-08-30
Is this during an installation, or what is the situation in which this occurs?

---

### Post by stevoo on 2008-08-30
You are leaving us in the dark ! 

More info ... 

you are saying spalsh screen. That is when the computer loads. 
So is it during loading when you try to login the computer crash ? 

Now install. Is it about a program ?  
Which one ? From where ? How do you do that ? Are your using wine ?

---

### Post by yogen on 2008-08-30
nopes..u aint getting me...

i'll tell you step wise...
1]I open the splash screen manager
2]then I click on the install button(to select the desired splash screen)
3]then when i select the screen and press the open button...the splash screen manager terminates...!!!

hope so u got me this time...

---

### Post by gmxgeek on 2008-08-30
Can you attatch a copy of the screen you are trying to install, or a link to it?

---

### Post by yogen on 2008-08-30
ya sure...

i tried this with two screens...

1]http://gnome-look.org/content/show.php/Carbono_usplash?content=87896

2]http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468

---

### Post by gmxgeek on 2008-08-30
Confirmed your error. Please open a terminal, and type 
```

gnome-splashscreen-manager

```

Proceed as normal, then post terminal output on crash.

---

### Post by yogen on 2008-08-30
crash report...


yogen@yogen-desktop:~/Desktop$ gnome-splashscreen-manager
/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `last_write': Unrecognized image file format
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `download_pixbuf'
	 from /usr/lib/ruby/1.8/open-uri.rb:32:in `open_uri_original_open'
	 from /usr/lib/ruby/1.8/open-uri.rb:32:in `open'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:191:in `download_pixbuf'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:199:in `create_thumbnail'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:209:in `install_new_splash_screen'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:192:in `install_new_splash_screen_dialog'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:60:in `on_button_install_new_splash_screen_clicked'
	 from /usr/lib/ruby/1.8/libglade2.rb:44:in `call'
	 from /usr/lib/ruby/1.8/libglade2.rb:44:in `connect'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:64:in `call'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:64:in `main'
	 from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:64:in `main'
	 from /usr/bin/gnome-splashscreen-manager:25
yogen@yogen-desktop:~/Desktop$

---

### Post by gmxgeek on 2008-08-30
I can't seem to track this one down. In the mean time, you could try using gnome-art and getting one of the ones in the archive

---

### Post by yogen on 2008-08-30
actually i had tried gnome art..
but in gnome art...when i select any of the options from the art menu...
gnome art directly starts downloading files and that hundreds in a queue...(it saya downloading file 1/1321......etc)

so i tried splash manager...

---

### Post by gmxgeek on 2008-08-30
It is downloading the list of themes from its archive. It shouldn't take too long.

---

### Post by yogen on 2008-08-30
does it downloads only the list(only file names)...or the whole file...???

---

### Post by gmxgeek on 2008-08-30
should download the list of files and a small png for a preview icon for each theme

---

### Post by yogen on 2008-08-30
a'right...thnk u million times dude...

and what about the xCursor...
it also has same kinda problem...but little different...
when i open the program and click the add button to add the file(s), now dialog box is opened(to browse for files)...even if u keep on clicking..!!!

---

### Post by gmxgeek on 2008-08-30
no problems

I will look into xCursor

---

### Post by yogen on 2008-08-30
so how will u add the downloaded files to xCursor...???

---

### Post by gmxgeek on 2008-08-30
what app are you using? i have found gcursor, but that is all. If that is what you are using, launch it from terminal
```

gcursor

```

and see if you get any errors

---

### Post by yogen on 2008-08-30
yes the same one...
in this program when i click the install button...no box dialog box opens...so there is no way for me to put the downloaded files in gcursor...!!!

---

### Post by gmxgeek on 2008-08-30
Does the terminal output anything about
```

 (gcursor:25785): libglade-WARNING **: could not find signal handler 'extract_theme'.

 (gcursor:25785): libglade-WARNING **: could not find signal handler 'open_theme_dir'.

 (gcursor:25785): libglade-WARNING **: could not find signal handler 'entry_selected'.

 (gcursor:25785): libglade-WARNING **: could not find signal handler 'size_changed'.

```

---

### Post by yogen on 2008-08-30
exactly...it gives perfectly the same output...!!!

---

### Post by gmxgeek on 2008-08-30
good. This is a known bug for gcursor.

[https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491](https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491)
See if any of the posts here help

---

### Post by yogen on 2008-08-30
so i can never use gcursor in my life...???

---

### Post by gmxgeek on 2008-08-30
Currently i haven't been able to find any fixes for it. You should be able to use the custom themes menu under Appearance in Preferences under System. Who knows, someone might release a bug fix for it some time, but until then, try to use the one in the system menu

---

### Post by yogen on 2008-08-30
a'right....anyways...thnx for the help...!!!

---

