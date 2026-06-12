---
title: "Sonance on Ubuntu Hoary"
date: 2005-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by macewan on 2005-03-02
[Sonance](http://sonance.aaronbock.net/) works on Ubuntu Hoary Hedgehog. If your interested in giving it a try then here’s how I did the Sonance dance. We’ll first assume that you have Hoary Hedgehog’ish flavor of Ubuntu, you have Mono & enough time on your hands to **** around. Yup, gnome-terminal is your friend so crankerup.

export CVSROOT=:pserver:anonymous@anoncvs.go-mono.com:/mono
cvs login
cvs co gst-sharp
cd gst-sharp
./autogen.sh
./configure –prefix=/usr
make
sudo make install
sudo cp /usr/bin/lib/pkgconfig/gst-sharp.pc /usr/lib/pkgconfig
svn checkout svn+ssh://anonymous@forgesvn1.novell.com/svn/sonance/trunk/sonance
anonymous *****for password*******
anonymous *****enter twice********
cd sonance
./autogen.sh –prefix=/usr
make
sudo make install

[Screenshot](http://www.macewan.org/screenshots/SonanceAbout.png)  of Sonance on Ubuntu Hoary Hedgehog.

---

### Post by hugh on 2005-05-09
Great howto. Thanks.

---

### Post by poofyhairguy on 2005-05-09
Move this one please mods.....

---

### Post by kassetra on 2005-05-09
[QUOTE=poofyhairguy]Move this one please mods.....[/QUOTE]

moved.  :)

---

### Post by bored2k on 2005-05-10
I think i have asked this with no reply but, what does make sonance any better than muine ? :?

---

### Post by vaskark on 2005-05-10
I received an error when compiling gst-sharp:
 > /usr/bin/mcs /out:play-mp3.exe /r:../gst-sharp/gst-sharp.dll -L ../gst-sharp /r:glib-sharp.dll ./PlayMp3.cs
error CS0006: Cannot find assembly `glib-sharp.dll'
Log:

Compilation failed: 1 error(s), 0 warnings
make[3]: *** [play-mp3.exe] Error 1
make[3]: Leaving directory `/home/jason/factory/gst-sharp/sample'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jason/factory/gst-sharp/sample'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jason/factory/gst-sharp'
make: *** [all] Error 2
What package am I missing (that contains glib-sharp.dll)? I'm on an updated hoary system.

---

### Post by ow50 on 2005-05-10
[QUOTE=vaskark]What package am I missing (that contains glib-sharp.dll)? I'm on an updated hoary system.[/QUOTE]
An indirect but educational do-it-yourself answer:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) -> Search the contents of packages

---

### Post by maddox on 2005-05-10
I have the same problem here when trying to compile gst-sharp.

"error CS0006: Cannot find assembly `glib-sharp.dll'"

but anyways, i found QuodLibet music player and i´m quite happy with it

---

### Post by MetalMusicAddict on 2005-05-10
[QUOTE=macewan]
export CVSROOT=:pserver:anonymous@anoncvs.go-mono.com:/mono
cvs login
cvs co gst-sharp
cd gst-sharp
./autogen.sh
./configure –prefix=/usr
make
sudo make install
sudo cp /usr/bin/lib/pkgconfig/gst-sharp.pc /usr/lib/pkgconfig
svn checkout svn+ssh://anonymous@forgesvn1.novell.com/svn/sonance/trunk/sonance
anonymous *****for password*******
anonymous *****enter twice********
cd sonance
./autogen.sh –prefix=/usr
make
sudo make instal[/QUOTE]
Sorry man but I dont understand what most of this ment. Is each line a command?

---

### Post by vaskark on 2005-05-11
[QUOTE=ow50]An indirect but educational do-it-yourself answer:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/") -> Search the contents of packages[/QUOTE]

Ok, I found that glib-sharp.dll is mentioned in libglib-cil and libglib2.0-cil, both of which I already have installed. I still receive the same error when running make.

---

### Post by Majlo on 2005-05-19
I have the Solution :-)
Sonance comes with a pre-built gst-sharp.dll assembly. To use it, configure sonance with –enable-bundled-gst-sharp
Then Sonance works great  \\:D/

---

### Post by bored2k on 2005-05-19
> checking for mono >= 1.0... Package mono was not found in the pkg-config search path.
Perhaps you should add the directory containing `mono.pc'
to the PKG_CONFIG_PATH environment variable
No package 'mono' found
checking for csc.exe... no
configure: error: You need to install either mono or .Net 

I just installed mono.. ?

---

### Post by bored2k on 2005-05-19
> yntax error, got token `OPEN_BRACE', expecting IDENTIFIER
generated/Structure.cs(11) error CS8025: Parsing error
syntax error, got token `OPEN_BRACE', expecting IDENTIFIER
generated/Tuner.cs(11) error CS8025: Parsing error
syntax error, got token `OPEN_BRACE', expecting IDENTIFIER
generated/XOverlay.cs(11) error CS8025: Parsing error
Compilation failed: 11 error(s), 0 warnings
make[2]: *** [gst-sharp.dll] Error 1
make[2]: Leaving directory `/opt/gst-sharp/gst-sharp'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/gst-sharp'
make: *** [all-recursive-am] Error 2 

someone ??

---

### Post by Majlo on 2005-05-20
Yes you must install mono packages .I have instaled this packages from backport :

mono mono-jit mono-utils mono-mcs mono-assemblies-arch mono-assemblies-base mono-common libgsf-cil libmono0 libmono-dev mono-devel mono-gac mono-jay

---

### Post by bored2k on 2005-05-20
[QUOTE=Majlo]Yes you must install mono packages .I have instaled this packages from backport :

mono mono-jit mono-utils mono-mcs mono-assemblies-arch mono-assemblies-base mono-common libgsf-cil libmono0 libmono-dev mono-devel mono-gac mono-jay[/QUOTE]
 From backports ? Ok thanx i'll try that now.

---

### Post by bored2k on 2005-05-20
```
make[3]: Entering directory `/opt/gst-sharp/sample'
/usr/bin/mcs /out:play-mp3.exe /r:../gst-sharp/gst-sharp.dll -L ../gst-sharp /r:glib-sharp.dll ./PlayMp3.cs
warning CS8029: Compatibility: Use -lib:ARG instead of --L arg
error CS0006: Cannot find assembly `glib-sharp.dll'
Log:

Compilation failed: 1 error(s), 1 warnings
make[3]: *** [play-mp3.exe] Error 1
make[3]: Leaving directory `/opt/gst-sharp/sample'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/gst-sharp/sample'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/gst-sharp'
make: *** [all] Error 2

```

Anyone ?

---

### Post by Majlo on 2005-05-20
Dont install gst-sharp ..Sonance comes with a pre-built gst-sharp.dll assembly. Follow this command :

svn checkout svn+ssh://anonymous@forgesvn1.novell.com/svn/sonance/trunk/sonance
anonymous *****for password*******
anonymous *****enter twice********
cd sonance
./autogen.sh --prefix=/usr --enable-bundled-gst-sharp
make
sudo make install

Try..

---

### Post by REBELinBLUE on 2005-05-20
can anyone help. I get this error

> checking for gtk-sharp-2.0 >= 1.9       gnome-sharp-2.0 >= 1.9  gnome-vfs-sharp-2.0 >= 1.9      glade-sharp-2.0 >= 1.9  gconf-sharp-2.0 >= 1.9  gapi-2.0 >= 1.9... Package gtk-sharp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk-sharp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk-sharp-2.0' found

configure: error: Library requirements (gtk-sharp-2.0 >= 1.9    gnome-sharp-2.0 >= 1.9  gnome-vfs-sharp-2.0 >= 1.9      glade-sharp-2.0 >= 1.9  gconf-sharp-2.0 >= 1.9  gapi-2.0 >= 1.9) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I've installed 

> mono-common mono-assemblies-base mono-jit libmono0 libmono-dev mono mono-assemblies-arch mono-mcs mono-gac mono-utils mono-jay mono-devel

but can't find gtk-sharp or anything similar

---

### Post by Majlo on 2005-05-20
You must  install package libgtk2.0-cil

---

### Post by REBELinBLUE on 2005-05-21
[QUOTE=Majlo]You must  install package libgtk2.0-cil[/QUOTE]

Thanks I managed to figure out what I needed after that but I'm stuck on 'gapi-2.0' but can only find gtk-sharp-gapi and thats not it :'(

---

### Post by Majlo on 2005-05-21
Then try install :
gtk-sharp-gapi-unstable

---

### Post by REBELinBLUE on 2005-05-23
[QUOTE=Majlo]Then try install :
gtk-sharp-gapi-unstable[/QUOTE]
 Yeh thanks, I managed to work out all the dependencies, however I get errors during build and now I'm stuck

> ./SqlGenerator.cs(32) error CS0122: 'message' is inaccessible due to its protection level
./AboutBox.cs(55) warning CS0169: The private method 'Sonance.AboutBox.OnButtonCloseClicked( object,  System.EventArgs)' is never used
./PlayerInterface.cs(361) warning CS0169: The private method 'Sonance.PlayerUI.SensitizeSearchButtons()' is never used
./PlayerInterface.cs(371) warning CS0169: The private method 'Sonance.PlayerUI.OnWindowPlayerDeleteEvent( object,  Gtk.DeleteEventArgs)' is never used
./PlayerInterface.cs(479) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuAboutActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(484) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuSearchBarActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(489) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuPreferencesActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(535) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuImportFolderActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(554) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuImportFilesActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(576) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuPlaylistClearActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(581) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuTrackPropertiesActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(586) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuNewPlaylistActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(598) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuNewSmartPlaylistActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(603) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuPlaylistRemoveActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(608) warning CS0169: The private method 'Sonance.PlayerUI.OnMenuPlaylistPropertiesActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(681) warning CS0169: The private method 'Sonance.PlayerUI.OnToggleButtonShuffleToggled( object,  System.EventArgs)' is never used
./PlayerInterface.cs(693) warning CS0169: The private method 'Sonance.PlayerUI.OnToggleButtonRepeatToggled( object,  System.EventArgs)' is never used
./PlayerInterface.cs(791) warning CS0169: The private method 'Sonance.PlayerUI.OnItemColumnsActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(796) warning CS0169: The private method 'Sonance.PlayerUI.OnItemRemoveActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(801) warning CS0169: The private method 'Sonance.PlayerUI.OnItemPropertiesActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(850) warning CS0169: The private method 'Sonance.PlayerUI.OnItemAddSelectedSongsActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(860) warning CS0169: The private method 'Sonance.PlayerUI.OnItemSourceDuplicateActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(865) warning CS0169: The private method 'Sonance.PlayerUI.OnItemSourceDeleteActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(876) warning CS0169: The private method 'Sonance.PlayerUI.OnItemSourcePropertiesActivate( object,  System.EventArgs)' is never used
./PlayerInterface.cs(56) warning CS0169: The private field 'Sonance.PlayerUI.spinner' is never used
./PlayerInterface.cs(61) warning CS0169: The private field 'Sonance.PlayerUI.plLoaderMax' is never used
./PlayerInterface.cs(61) warning CS0169: The private field 'Sonance.PlayerUI.plLoaderCount' is never used
./GstPlayer.cs(83) warning CS0169: The private field 'Sonance.GstPlayer.playing' is never used
./GstPlayer.cs(87) warning CS0169: The private field 'Sonance.GstPlayer.timeoutHandle' is never used
./Utilities.cs(33) warning CS0169: The private field 'Sonance.Error.message' is never used
./Utilities.cs(34) warning CS0169: The private field 'Sonance.Error.e' is never used
./PlaylistView.cs(40) warning CS0169: The private field 'Sonance.PlaylistColumn.view' is never used
./PlaylistView.cs(41) warning CS0169: The private field 'Sonance.PlaylistColumn.datafunc' is never used
./PlaylistView.cs(521) warning CS0169: The private method 'Sonance.PlaylistView.PlayingTrackInfo()' is never used
./PlaylistView.cs(220) warning CS0169: The private field 'Sonance.PlaylistView.dragEntries' is never used
./Dialogs.cs(81) warning CS0169: The private field 'Sonance.InputDialog.dialog' is never used
./TrackProperties.cs(79) warning CS0169: The private method 'Sonance.TrackProperties.OnButtonCloseClicked( object,  System.EventArgs)' is never used
./Preferences.cs(66) warning CS0169: The private method 'Sonance.PreferencesWindow.OnButtonCancelClicked( object,  System.EventArgs)' is never used
./Preferences.cs(71) warning CS0169: The private method 'Sonance.PreferencesWindow.OnButtonOkClicked( object,  System.EventArgs)' is never used
./Preferences.cs(77) warning CS0169: The private method 'Sonance.PreferencesWindow.OnButtonLibraryChangeClicked( object,  System.EventArgs)' is never used
./Preferences.cs(97) warning CS0169: The private method 'Sonance.PreferencesWindow.OnButtonLibraryResetClicked( object,  System.EventArgs)' is never used
./LibraryTransactions.cs(172) warning CS0169: The private field 'Sonance.FileLoadTransaction.allowLibrary' is never used
./QueryBuilder.cs(152) warning CS0169: The private field 'Sonance.QueryBuilderMatchRow.valueBox' is never used
./QueryBuilder.cs(161) warning CS0169: The private field 'Sonance.QueryBuilderMatchRow.canDelete' is never used
./QueryBuilderModel.cs(230) warning CS0169: The private field 'Sonance.TracksQueryModel.fields' is never used
Compilation failed: 1 error(s), 44 warnings
make[2]: *** [sonance.exe] Error 1
make[2]: Leaving directory `/home/stephen/sonance/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stephen/sonance/src'
make: *** [all-recursive] Error 1

---

### Post by Unwiseone on 2005-05-24
[QUOTE=REBELinBLUE]Yeh thanks, I managed to work out all the dependencies, however I get errors during build and now I'm stuck[/QUOTE]

I'm having the same exact problem as described in the above post. Anyone figure out a workaround of fix for this?

---

### Post by bored2k on 2005-05-24
[QUOTE=Unwiseone]I'm having the same exact problem as described in the above post. Anyone figure out a workaround of fix for this?[/QUOTE]
 I tried hard until I gave up.. I tried to get this working for two days..

---

### Post by REBELinBLUE on 2005-05-24
[QUOTE=bored2k]I tried hard until I gave up.. I tried to get this working for two days..[/QUOTE]
 Yeh I've given up, I took a look through some C# .NET documentation to see if I could figure it out looking at exception handling and scope but I can't see anything wrong. Looks like we've just going to have to wait for a new revision, shame it looks really good :(

---

### Post by ounn on 2005-05-24
yeh, exactly the same problem here. No one knows a magical solution for this?I realy like to give a try to sonance.

ounN

---

### Post by ounn on 2005-05-25
I've finaly managed a away to compile sonance.

edit SqlGenerator.cs
and replace this line
		public extern SqlGeneratorException(string message) : base(message);
with this
 		public const string message2 = "JJGH";
		public extern SqlGeneratorException(string message2) : base(message2);

then compile with
./configure --prefix=/usr --enable-bundled-gst-sharp
make
make install

I realy dont know what this means, but at least it compile

---

### Post by mattisking on 2005-05-28
[QUOTE=ounn]I've finaly managed a away to compile sonance.

edit SqlGenerator.cs
and replace this line
		public extern SqlGeneratorException(string message) : base(message);
with this
 		public const string message2 = "JJGH";
		public extern SqlGeneratorException(string message2) : base(message2);

then compile with
./configure --prefix=/usr --enable-bundled-gst-sharp
make
make install

I realy dont know what this means, but at least it compile[/QUOTE]
 Hey, thanks ounn. That worked perfectly for me. I've been wanting to try Sonance for a long time and this works (so far) even under Breezy.

---

### Post by vaskark on 2005-05-30
Is the album art displaying for people? It isn't for me.

---

### Post by Unwiseone on 2005-06-08
[QUOTE=ounn]I've finaly managed a away to compile sonance.

edit SqlGenerator.cs
and replace this line
		public extern SqlGeneratorException(string message) : base(message);
with this
 		public const string message2 = "JJGH";
		public extern SqlGeneratorException(string message2) : base(message2);

then compile with
./configure --prefix=/usr --enable-bundled-gst-sharp
make
make install

I realy dont know what this means, but at least it compile[/QUOTE]

Thanks alot man! You know know how long I was struggling with this!   :grin:

---

### Post by delsdog on 2005-08-13
[QUOTE=ounn]I've finaly managed a away to compile sonance.

edit SqlGenerator.cs
and replace this line
		public extern SqlGeneratorException(string message) : base(message);
with this
 		public const string message2 = "JJGH";
		public extern SqlGeneratorException(string message2) : base(message2);

then compile with
./configure --prefix=/usr --enable-bundled-gst-sharp
make
make install

I realy dont know what this means, but at least it compile[/QUOTE]
 I'd really like to try this but I haven't a clue where SqlGenerator.cs is (I don't think search for files is working properly), and when I try the original methodology I get told I don't have gstreamer-0.8, which I know I do have.

---

### Post by Bo Rosén on 2005-08-14
[QUOTE=delsdog]I'd really like to try this but I haven't a clue where SqlGenerator.cs is [/QUOTE]

It should be in ~/svn/sonance/src 
i.e in a directory called src (short for source) in the sonance directory.

Good luck, this worked for me.

---

### Post by Bo Rosén on 2005-08-14
Importing my libary now, all 5000+ tracks. I've noticed the Rating and Play Count fields display the album name. Also the m4a's bought with Sharpmusique usually have a track entry of '0'. Anyone else see this?

[color=Red]Update[/color]: Looks like the m4a-files had horribly bad metadata. I installed itunes on my windows partion and corrected that part at least.[color=Black] [/color]

---

### Post by delsdog on 2005-08-14
[QUOTE=Bo Rosén]It should be in ~/svn/sonance/src 
i.e in a directory called src (short for source) in the sonance directory.

Good luck, this worked for me.[/QUOTE]

Ok, got that done thanks, and it seems to be building nicely until it decides that I still don't have gstreamer-0.8, and that I should add it to the PKG_CONFIG_PATH environment variable.

Excuse my stupidity, but how do I do that? I know I have gstreamer-0.8 and I would have thought it would already be in the PATH, so now I'm stuck again.  :|

---

### Post by Bo Rosén on 2005-08-14
[QUOTE=delsdog]
Excuse my stupidity, but how do I do that? I know I have gstreamer-0.8 and I would have thought it would already be in the PATH, so now I'm stuck again. :|[/QUOTE]

Finding compiling unfinished software difficult hardly counts as stupidity.
At a guess, what you need is libgstreamer0.8-dev but I'm probably not the right person to ask ;)

 ```
sudo apt-get install libgstreamer0.8-dev
```

Hope that solves it.

[color=Red]Update: [color=Black]I also have libgstreamer-gconf0.8-dev and libgstreamer-plugins0.8-dev installed. Not sure if they are needed though, but try them if you still have problems.

Good luck
[/color][/color]

---

### Post by delsdog on 2005-08-14
> **Bo Rosén]Finding compiling unfinished software difficult hardly counts as stupidity.
At a guess, what you need is libgstreamer0.8-dev but I'm probably not the right person to ask  said:**
> Update: [color=Black]I also have libgstreamer-gconf0.8-dev and libgstreamer-plugins0.8-dev installed. Not sure if they are needed though, but try them if you still have problems.

Good luck
[/color][/color]
 I did as you said, and it certainly helped, although I then got told that there were other files that were needed (again I knew I had them already) so I applied your solution and added the dev versions, and it all seemed to work :)

Thanks for the help.

Now what happens if I don't like the program ;)

---

### Post by domesticatewhat on 2005-08-14
Well everything compiled and its running, however, quite a few things don't work.

I have the same problem with the rating and play count section. Search does not work and album info isn't even an option.

---

### Post by delsdog on 2005-08-14
[QUOTE=domesticatewhat]Well everything compiled and its running, however, quite a few things don't work.

I have the same problem with the rating and play count section. Search does not work and album info isn't even an option.[/QUOTE]
This is an early version though, I'm willing to hold my opinion till I see the newly renamed version (Banshee) running.

---

### Post by Bo Rosén on 2005-08-15
Glad you got it working, delsdog. 

I played around with it a bit yesterday, not that there was much to play around with, and it's definitely not ready for normal use for a while yet. Not that it claims to be, but it's fun to take a look at new software sometimes to see for yourself what people are talking about. I'll stick with Rhythmbox for a while yet (now, maybe I should try out the new version of that...) :p

---

### Post by SKLP on 2005-08-16
Banshee (latest CVS) works fine here on latest breezy ;-)

---

### Post by varunus on 2005-08-16
Trying the latest CVS of banshee, ./configure said that mono 1.1.8 was required...is it ok to just change the configure script to use mono 1.1.7?  Or will this not work...I'm willing to tinker a bit if necessary.  (Or does someone have magical mono 1.1.8 packages for Hoary?)

---

### Post by vaskark on 2005-08-16
Can someone post some shots of Banshee?

---

### Post by nehalem on 2005-08-16
I'm curious too about this program.  Is it any better than rhythmbox yet?  I have really been impressed with mono apps so far.

---

### Post by delsdog on 2005-08-18
I third the request for some screenshots of Banshee in action.

---

### Post by el toro on 2005-08-20
Welll...I'm not sure I attached the file correctly but here's a shot of the latest Banshee CVS running on my Breezy install.  There's been a lot of progress so far, but still a ways to go (can't really create playlists, etc.).  Looks like it will be a good app once it has matured a bit.

---

### Post by macewan on 2005-09-24
[QUOTE=ounn]I've finaly managed a away to compile sonance.

edit SqlGenerator.cs
and replace this line
        public extern SqlGeneratorException(string message) : base(message);
with this
         public const string message2 = "JJGH";
        public extern SqlGeneratorException(string message2) : base(message2);

then compile with
./configure --prefix=/usr --enable-bundled-gst-sharp
make
make install

I realy dont know what this means, but at least it compile[/QUOTE]


excellent, this works like magic

---

