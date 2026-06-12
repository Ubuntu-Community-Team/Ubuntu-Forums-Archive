---
title: "HOWTO: Wine made easy with Wine-Doors (GNOME Integration and More)"
date: 2007-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Espreon on 2007-07-02
Wine-Doors is a Wine management tool for the GNOME desktop, it is still in development but is pretty functional and stable. Also I would not recommend Wine to Linux noobs w/o also recommending Wine-Doors.

**Vids on Youtube:**

search for wine doors or wine-doors

**Features include:**

GNOME Menu integration: You get a Wine menu under the Applications Menu, which all Wine programs put entries in as it were the Start menu.

Nautilus Integration: All .exe files will have the default action of the .exe being run in Wine.

Respotories: Wine-Doors lets you use respos to install Windows software (Wine-Doors comes with 3), similar to Apt-Get respos.

Cedega Integration: Allows one to adjust Cegeda settings and profiles within Wine-Doors.

Bottles (Still under development, needs tweaking to work): Just like CrossOver Bottles, this feature is supposed to work with Cedega and CrossOver bottle too.

Wine Configurer: Allows one to Configure Wine with Wine-Doors.

**Features that are under Development but do not work:**

Wine process manager: I guess a Task Manager clone for Wine processes.

Wine Reboot Option: Reboots Wine.

Help Feature: Offers Help.


[b]More Info: [http://www.wine-doors.org/wordpress](http://www.wine-doors.org/wordpress)
For Even more info: [http://www.wine-doors.org/trac](http://www.wine-doors.org/trac)[/b]

**How to install:**


**SVN (I recommend you Install SVN since the SVN version is more functional):**

First fire up the terminal and take care of the dependencies (I assume you are using Feisty)
If not go to this page and see if you have the listed dependencies if not take care of them: [http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3))

```
sudo apt-get install orange subversion cabextract
```

Second grab the latest Revision of Wine-Doors:

```
svn checkout [http://www.wine-doors.org/svn/trunk](http://www.wine-doors.org/svn/trunk)
```

Third change the directory to the trunk folder in your home folder (it contains the Revision of Wine-Doors you grabbed):

Replace "yourhomedirectory" with the name of your home folder

```
cd '/home/"yourhomedirectory"/trunk'
```

Fourth initiate the install script:

python setup.py install

5th: If all went well goto Applications>System Tools>Wine-Doors and click it

6th: Now enter your name, and if you have a valid license to use Windows click I have a valid Microsoft Windows (tm) license. (you will need to click it if you have want to install IE and other Windows libraries).
When a bunch of windows pop up do not click anything since they are automated.

7th: if all went well you should see the Wine menu in the Applications menu and the Wine-Doors menu!
Pat yourself on the back, you deserve it.

**ALSO WHEN YOU CONFIGURE Wine-Doors NEVER CLICK THE : Show Wine Menu (even when it is unclicked it will make the Menu dissappear, only click if there is no Wine menu)**


**Stable:**

1st: fire up the terminal and take care of the dependencies:

```
sudo apt-get install orange cabextract
```

2nd: get  the .deb and install

Replace yourhomedirectory with the name of your home folder

```

wget http://www.wine-doors.org/releases/wine-doors_0.1-1_all.deb
dpkg --install /home/yourhomedirectory/wine-doors_0.1-1_all.deb

```

3rd execute: goto >Applications>System Tools>Wine-Doors click it

4th: Enter your info and if you have a Windows license click I have a valid Microsoft Windows (tm) license.

5th Don't click any windows that pop up since they are automated.

6th: if all went well you should See the Wine menu under the Applications menu and the Wine-Doors window.

7th: pat your self on the back. and remeber never click the Show Wine menu button unless the Menu is not present.

---

### Post by frodon on 2007-07-03
Full wine guide with description of the other tools available like winetools, winecfg or winesetuptk here :
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by vvlist on 2007-07-06
Wine-Doors 0.1 was released! Get it [here]("http://www.wine-doors.org/wordpress/?page_id=3"). Believe me, it is worth a try!

---

### Post by Calash on 2007-07-06
I installed Wine-Doors this morning...it worked fairly well.  I got IE running fine, but the one site I need it to work on did not function correctly.  I am guessing it was trying to write someplace it should not have (It is an ActiveX VPN Tunnel )  This is less an issue with Wine-Doors and more with the IE package.

Other than that it worked great...it is nice to have IE there for web development.

---

### Post by KYhillbilly2006 on 2007-07-08
I tried installing wine-doors but I get this error:

Installing system base libraries
Symlinking executable
Creating initial preferences
Checking dependencies
  wine . . .  Found
  cabextract . . .  Found
  tar . . .  Found
  orange . . .  Found
  ps . . .  Found
  pygtk . . .  Found
  pycairo . . .  Found
  rsvg . . .  Not found
One of the required modules for the wine-doors user interface is missing
the wine-doors command line interface is available, for more information
try running: /home/family/bin//wine-doors --help

It looks like I don't have the rsvg files installed.  I've checked to see if I have all the dependencies and I have everything on the list.  i tried searching for rsvg with the Synaptic and installed all I seen.  Still not coming up with the rsvg.  Where do I get this at?

---

### Post by Espreon on 2007-07-09
Upgrade to Feisty or install librsvg (in Synaptic after searching for rsvg [I checked this in Feisty though])

---

### Post by sefs on 2007-07-09
I keep getting asked about an install.ahk script, and then when i click yes to create it tells me I do not have permission to create this scrite somewhere in the .wine-doors/apppack directory structure.

---

### Post by Espreon on 2007-07-09
Very weird, which Ubuntu version are you using (version and flavor (U,Ku,Xu)

---

### Post by KYhillbilly2006 on 2007-07-09
[QUOTE="Espreon"]Upgrade to Feisty or install librsvg (in Synaptic after searching for rsvg [I checked this in Feisty though[/QUOTE]

I don't want to upgrade to Fiesty right now and there is no librsvg in Synpatic.  There is a librsvg2-2 that I have installed already.  I did a search for librsvg and everything that had that "ive installed but still when I try to install wine-doors it says it can't find it.

---

### Post by andrek on 2007-07-09
While installing Call of Duty, I got an error :
IOError: [Errno 2] Nie ma takiego pliku ani katalogu *(there's no such file or directory)*: u'scripts/cod.sh'
Traceback (most recent call last):
  File "/usr/share/wine-doors/src/ui.py", line 663, in fade_cell
    treeiter = self.model.get_iter( path )
ValueError: invalid tree path

In app's window it stucked on 'Installing desktop menus'

and it seems to be dead right now..

(downloaded from svn)

---

### Post by erwall on 2007-07-09
Install seemed to go fine but when I go to startup the program in Apps --> System Tools nothing happens.  Uninstalled it w/the script and d/l'd the .deb file from wine-doors.com and installed fine and still the same thing, any ideas?

---

### Post by andrek on 2007-07-10
Try opening it in terminal by typing wine-doors [ without being a root ]

---

### Post by erwall on 2007-07-10
It opens from the command line and I type in my name and check the box about the MS license and click Proceed and that's it, nothing happens.  It seems to have a problem creating the wine-drive?

---

### Post by dxdemetriou on 2007-07-10
Anybody knows how can I change language with wine-doors? I have an english operating system that supports greek.
When I use some program with wine-doors to see a file name with greek characters, aren't shown like nothing is written.
I had installed before the ies4linux without the wine-doors, with the old way, and there the file names are shown correctly
thanks

---

### Post by adarkmethod on 2007-07-10
ERROR: Cannot find system or user preferences, No repositories are configured
You can create a preferences file in either /etc/wine-doors/preferences.xml
or ~/.wine/wine-doors/preferences.xml by following this example: 
[http://www.wine-doors.org/trac/wiki/ConfigurationFile](http://www.wine-doors.org/trac/wiki/ConfigurationFile)


anyone got an idea?

---

### Post by bamend on 2007-07-11
Has anyone been able to install Dreamweaver and Flash?  My install always hangs up.  I've uninstalled Wine-doors and reinstalled it but still no luck.

---

### Post by DanielDunn on 2007-07-11
> **bamend said:**
> Has anyone been able to install Dreamweaver and Flash?  My install always hangs up.  I've uninstalled Wine-doors and reinstalled it but still no luck.

I have had the same issues. I am using Feisty 64bit Ubuntu

---

### Post by Espreon on 2007-07-12
> **bamend said:**
> Has anyone been able to install Dreamweaver and Flash?  My install always hangs up.  I've uninstalled Wine-doors and reinstalled it but still no luck.

Do you need the .exe files that install Flash and DreamWeaver.

---

### Post by DanielDunn on 2007-07-12
> **Espreon said:**
> Do you need the .exe files that install Flash and DreamWeaver.

where do i put the .exe files so that wine-doors sees them?

---

### Post by Pheodax on 2007-07-13
I think the SVN is down, but I'll try the stable. Thanks for the guide! :)

---

### Post by krul on 2007-07-14
Very good initiative...I really like the program.

Is there also a one-click procedure to uninstall the Wine programs??

---

### Post by nikoPSK on 2007-09-20
Peggloe won't work in wine for me... I get sound but no image...:confused::(

---

### Post by nikoPSK on 2007-09-22
Doesn't work for me... :( 

Check my wine-doors thread.:confused:

---

### Post by Pedro0727 on 2007-11-18
tnx for the good tutorial about wine.. its very easy to understand and easy to follow. Again tnx  a lot Espreon.. Mabuhay k!!

---

### Post by Batman77 on 2008-01-14
I think it is a CON,, I tried to install dreamweaver with it,, but all it does is install some stock trading programme,,  how do I remove Wine Doors?

---

### Post by Espreon on 2008-01-15
> **Batman77 said:**
> I think it is a CON,, I tried to install dreamweaver with it,, but all it does is install some stock trading programme,,  how do I remove Wine Doors?

Its one of those things called a bug, but which method did you use to install Wine-Doors?

---

### Post by diablo75 on 2008-01-24
> **KYhillbilly2006 said:**
> I tried installing wine-doors but I get this error:

Installing system base libraries
Symlinking executable
Creating initial preferences
Checking dependencies
  wine . . .  Found
  cabextract . . .  Found
  tar . . .  Found
  orange . . .  Found
  ps . . .  Found
  pygtk . . .  Found
  pycairo . . .  Found
  rsvg . . .  Not found
One of the required modules for the wine-doors user interface is missing
the wine-doors command line interface is available, for more information
try running: /home/family/bin//wine-doors --help

It looks like I don't have the rsvg files installed.  I've checked to see if I have all the dependencies and I have everything on the list.  i tried searching for rsvg with the Synaptic and installed all I seen.  Still not coming up with the rsvg.  Where do I get this at?

> **adarkmethod said:**
> ERROR: Cannot find system or user preferences, No repositories are configured
You can create a preferences file in either /etc/wine-doors/preferences.xml
or ~/.wine/wine-doors/preferences.xml by following this example: 
[http://www.wine-doors.org/trac/wiki/ConfigurationFile](http://www.wine-doors.org/trac/wiki/ConfigurationFile)


You have to save the file to the desktop or some other location, and not just "run" it.  The deb file is references several times, but seems to disappear from the tmp cache after a short moment after it's been accessed once.  I got this same error, but solved it by simply saving the file to the desktop and double clicking on it from there.

Now...if someone could help me with something real quick:

I just installed Dreamweaver 8 using Wine-Doors, and it works.  Except for one thing.  It doesn't seem to access the Internet properly, so it does not connect to my server like I want it to.  I don't know what to do or try to troubleshoot this issue...  PLEASE HELP!

---

### Post by DAaaMan64 on 2008-01-27
I think the SVN URL may have changed, I set it to this to install wine-doors:  [http://www.wine-doors.org/svn/wine-doors/trunk/](http://www.wine-doors.org/svn/wine-doors/trunk/)

---

