---
title: "Lazarus &amp; FPC"
date: 2005-07-06
forum: Programming Talk
---

### Post by Rodrigo on 2005-07-06
Ok, so I installed ALL the fpc packages. (2.0.0)
I download Lazarus from here: [http://packages.debian.org/experimental/devel/lazarus](http://packages.debian.org/experimental/devel/lazarus)

I get all libgdk-pixbuf stuff " sudo apt-get install libgdk-pixbuf-dev libgdk-pixbuf-gnome-dev libgdk-pixbuf-gnome2 libgdk-pixbuf2 "  :smile: 

ok...

did a dpkg over lazarus (becouse "he" said he need all the fpc 0.9.4, but I got the 2.0.0, go figure)

best solution?... dpkg -i --force-depends lazarusblabla.deb
and it works, saw the IDE, niiiiiceeee, make some buttons, type some code... ok.. lets run my first app on lazarus (at last!!!!).

Then the dream was gonne....

The "ONLY"  problem (for the moment) I have right now is that: when I want to run an app, it tells me that it cant find " Intefaces" Unit...
OOOhhh, ok... I have to setup the fpc source directory...

but... (this sound stupid) guess what... I cant find it  *hehe*.... I guess is some of the /usr/lib/fpc/2.0.0/  
but Im not sure, I really REALLY have no Idea.

Any body has a solution or may be can post the PROPER instalation of lazarus and fpc????

thanks 4 your help. 

Adios

---

### Post by Rodrigo on 2005-07-06
Lazarus Project FAQ (Frequently Asked Questions)...

1st solution....

When compiling a project it says: project1.lpr(6,13) Fatal: Can't compile unit INTERFACES, no sources available

This means, that one of the dependent units of interfaces.ppu has changed. This can have several reasons:

   1. If you installed via rpm: The fpc rpm is not the right one for the lazarus rpm. The right fpc rpm can be downloaded from the lazarus site.
   2. Check if the compiler is using the right config file. The normal installation creates /etc/fpc.cfg. But fpc also searches for ~/.ppc386.cfg, ~/.fpc.cfg, /etc/ppc386.cfg and it uses only the first it finds.
      Hint: You can see which config file is used with 'ppc386 -vt bogus'
   3. You have two lazarus source directories and the lazarus path is still pointing to the old one. Check Environment -> Environment options -> Files -> Lazarus Directory.
   4. You compiled your own fpc and forgot to compile lazarus.


second solution.....

I can not compile a project. I get: /tmp/project1.lpr(6,13) Fatal: can't find unit INTERFACES

Make sure that the LCL package is used by your project. Open Project -> Project Inspector and add a new requirement -> Package LCL.


Hope this works, I cant test it right now, I'll post if that work.

---

### Post by Rodrigo on 2005-07-08
Weeeeeell......, didnt work

Any help?

---

### Post by Rodrigo on 2005-07-12
No one really knows how to HELP ME?!?!?!?!??

---

### Post by atilasendil on 2005-08-02
I guess I have the same problem here :

---------------------------------------------------------------------------------------------------------------
[FONT=Courier New]
[FONT=Courier New]$ lazarus
[WARNING] *******************************************************
[WARNING] **                                                   **
[WARNING] ** Multibyte character encodings (like UTF8) are not **
[WARNING] ** supported at the moment.                          **
[WARNING] ** For full keyboard event support, make sure that   **
[WARNING] ** the LANG environment var has no UTF8              **
[WARNING] **                                                   **
[WARNING] *******************************************************
TApplication.IconChanged - TODO: convert this message...no implementation in gtk or win32
NOTE: editor options config file not found - using defaults
NOTE: miscellaneous options file not found - using defaults
NOTE: codetools config file not found - using defaults

NOTE: FPC Source Directory not set! (see Environment Options)

NOTE: Could not create Define Template for Free Pascal Sources
NOTE: help options config file not found - using defaults
TMainIDE.DoNewProject A
TMainIDE.DoNewEditorFile A NewFilename=
TPascalParserTool.BuildTree B OnlyIntf=False  project1.lpr
[TCustomFormEditor.CreateComponent] Class='TForm'
TPascalParserTool.BuildTree B OnlyIntf=False  project1.lpr
TMainIDE.DoNewEditorFile end unit1.pas
TMainIDE.DoNewProject end[/FONT][/FONT]

---------------------------------------------------------------------------------------------------------------
can anyone help me ? ? ?
thank you in advance :-)

---

### Post by atilasendil on 2005-08-10
Well;
the problem is solved at least for me ...
I had only downloaded 2 packages and had forgot the sources package;
I had also installed the dependency packages you mentioned ...
and I can code and run now ...
the address I downloaded is :
[http://sourceforge.net/project/showfiles.php?group_id=89339](http://sourceforge.net/project/showfiles.php?group_id=89339) 

and the packages are :
fpc-2.0.0-0.i586.rpm
fpcsrc-2.0.0-0.i386.rpm
lazarus-0.9.8-fpc_2.0.0_0.i386.rpm

I also downloaded :
fpc-docs-2.0.0-0.i586.rpm
but have not installed yet ...

and thanks to others in forums and the ubuntuguide I made .deb files and installed and am coding pascal in gui now :-)

---

