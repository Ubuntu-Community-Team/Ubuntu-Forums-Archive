---
title: "HOWTO: Install DevilsPie 0.10 (the latest version)"
date: 2005-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by ghostintheshell on 2005-07-15
Hi,

For people who don't like to wait the latest package, here's my how-to for installing _**DevilsPie 0.10**_.

- First of all, remove your actual version of DevilsPie (If you already have one ;)) from synaptic or dpkg ...

- As usual, download the tar.gz file: [here]("http://www.burtonini.com/computing/devilspie-0.10.tar.gz") (from the [official web site]("http://www.burtonini.com/blog/computers/devilspie"))
- Untar it
- I use to copy all my sources files to */usr/local/src/* (to keep the sources and easily uninstall with the *make uninstall* command when a new version is available)
- Then go to */usr/local/src/devilspie-0.10* (or the directory where you put the sources)

- Try to configure: [color=Navy]./configure --prefix=/usr[/color]

You should meet a strange error: *[color=Red]checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool[/color]*

Ok, here's the solution:
(need to be root -> sudo)
- [color=Navy]sudo perl -MCPAN -e shell[/color] (would run CPAN module of Perl)
- [color=Navy]install XML::Parser[/color] (would install XML::Parser and all of its dependencies)
- [color=Navy]bye[/color] (would exit CPAN)

Ah ah, try again ... 
- [color=Navy]./configure --prefix=/usr[/color]

Ok right now!

- [color=Navy]make[/color]
- [color=Navy]sudo make install[/color]

- Optional: [color=Navy]make clean[/color] (would delete useless compiled files -> disk storage)
- Optional (later ;)): [color=Navy]sudo make uninstall[/color] (would reverse the process -> delete all installed files)

If you don't have already a *.devilspie.xml* file in your home directory (*~/.devilspie.xml*), no problemo:
- Copy the *sample-config.xml* file which is in the source directory (mine is */usr/local/src/devilspie-0.10/sample-config.xml*) in your home directory
- Rename it as* .devilspie.xml*
- A chown + a chmod on the file (*~/.devilspie.xml*) to become the owner and give you the rights on the file

Now, you can edit it with your rules.

To launch devilspie at the startup: 
- Go to the Gnome menu: System / Preferences / Sessions / Startup Programs 
- Then add an entry: devilspie with priority: 45

For people asking me why use DevilsPie? He he ... For a lot of things :p
I personally use it for:
- XMMS (to complete the '[status docklet]("http://www.hellion.org.uk/xmms-status-plugin/")' plugin action => not visible in the task bar and the pager)
- Thunderbird (to automagically put it on 2nd desktop at the top left border of the screen) 
- Eterm (to  [merge a terminal with the desktop]("http://www.ubuntuforums.org/showthread.php?t=36811&highlight=Eterm") => not visible in the task bar and the pager, under all windows and visible on all desktops = pinned).

Here's my* .devilspie.xml* file (take it as a sample):

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">

<devilspie>

	<flurb name="Print Window Names">
		<matchers>
		<!-- this is a matcher which always returns true. The full class name must be used -->
		<matcher name="DevilsPieMatcherAlways"/>
		</matchers>
		<actions>
		<!-- this action prints out the window and application name -->
		<action name="DevilsPieActionDebug"/>
		</actions>
	</flurb>

	<flurb name="XMMS">
		<matchers>
		<matcher name="DevilsPieMatcherWindowName">
			<property name="application_name" value="XMMS"/>
		</matcher>
		</matchers>
		<actions>
		<action name="DevilsPieActionHide">
			<property name="skip_tasklist" value="TRUE"/>
			<property name="skip_pager" value="TRUE"/>
		</action>
		</actions>
	</flurb>

	<flurb name="Eterm">
		<matchers>
		<matcher name="DevilsPieMatcherWindowName">
			<property name="application_name" value="Eterm"/>
		</matcher>
		</matchers>
		<actions>
			<action name="DevilsPieActionSetWorkspace">
				<property name="pinned" value="TRUE"/>
			</action>
			<action name="DevilsPieActionHide">
				<property name="skip_tasklist" value="TRUE"/>
				<property name="skip_pager" value="TRUE"/>
			</action>
			<action name="DevilsPieActionLayer">
				<property name="above" value="FALSE"/>
			</action>
		</actions>
	</flurb>

	<flurb name="Thunderbird">
		<matchers>
			<matcher name="DevilsPieMatcherWindowName">
				<property name="application_name" value="mozilla-thunderbird-bin"/>
			</matcher>
		</matchers>
		<actions>
			<action name="DevilsPieActionSetWorkspace">
				<property name="workspace_index" value="2"/>
			</action>
			<action name="DevilsPieActionSetGeometry">
				<property name="xoffset" value="0"/>
				<property name="yoffset" value="0"/>
			</action>
		</actions>
	</flurb>

</devilspie>
```

And now enjoy editing your own rules :cool:

---

### Post by aran384 on 2005-08-06
ok what does this do then???

what do u mean > For people who don't like to wait the latest package, here's my how-to for installing DevilsPie 0.10.

---

### Post by krusbjorn on 2005-08-06
The devilspie package in the apt repositories is version 0.7. If you want the latest version (0.10) you need to install it manually.

---

### Post by qalimas on 2005-08-21
Is there a page listing all the possible options?

---

### Post by arnieboy on 2005-08-21
[QUOTE=qalimas]Is there a page listing all the possible options?[/QUOTE]
does this latest version of devilspie override "show desktop"? in other words, will eterm stay on even if i click on show desktop?

---

### Post by ghostintheshell on 2005-08-21
[QUOTE=arnieboy]does this latest version of devilspie override "show desktop"? in other words, will eterm stay on even if i click on show desktop?[/QUOTE]

not in my case.

---

### Post by arnieboy on 2005-08-21
[QUOTE=ghostintheshell]not in my case.[/QUOTE]
well then I guess the upgrade isnt worth it. Thanks anyway for the HowTo

---

### Post by ghostintheshell on 2005-08-21
[QUOTE=qalimas]Is there a page listing all the possible options?[/QUOTE]

I don't think, no.

I used the sources to discover the available options.

But you can ask more infos directly to Ross Burton, the programer of this great app.
-> [http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

Enjoy.

---

### Post by ghostintheshell on 2005-10-31
since the 0.13+ version of devilspie, the xml syntax was replaced by the "s-expressions" syntax.

here's the conversion of my sample (first post):

- create a *.devilspie* directory in your home folder
```
mkdir ~/.devilspie
``` 
_eterm:_
- create a *eterm.ds* file in the *~/.devilspie* folder and put this in:
```
(if (is (application_name) "Eterm") (begin skip_tasklist skip_pager pin below))
``` 

_thunderbird:_
- create a *thunderbird.ds* file in the *~/.devilspie* folder and put this in:
```
(if (is (application_name) "mozilla-thunderbird-bin") (begin geometry "+0+0" set_workspace 2))
``` 
restart devilspie with the -a option:
```
killall devilspie
devilspie -a &
``` 
all available actions are listed in the */src/parser.c* file available in the in the *devilspie-0.1x.tar.gz* archive.

enjoy.

---

### Post by maxdevis on 2006-01-31
i want that BMP starts at workspace 4.
what do i wrong?

<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">

<devilspie>

	<flurb name="Thunderbird">
		<matchers>
			<matcher name="DevilsPieMatcherWindowName">
				<property name="application_name" value="mozilla-thunderbird-bin"/>
			</matcher>
		</matchers>
		<actions>
			<action name="DevilsPieActionSetWorkspace">
				<property name="workspace_index" value="2"/>
			</action>
			<action name="DevilsPieActionSetGeometry">
				<property name="xoffset" value="0"/>
				<property name="yoffset" value="0"/>
			</action>
		</actions>
	</flurb>

	<flurb name="BMP">
		<matchers>
			<matcher name="DevilsPieMatcherWindowName">
				<property name="application_name" value="beep-media-player"/>
			</matcher>
		</matchers>
		<actions>
			<action name="DevilsPieActionSetWorkspace">
				<property name="workspace_index" value="4"/>
			</action>
			</action>
		</actions>
	</flurb>


he gives me also this error:

** (devilspie:9941): WARNING **: Could not parse configuration: Fout in regel 33 teken 13: Element 'action' is gesloten, maar op dit moment is element 'actions' open

---

