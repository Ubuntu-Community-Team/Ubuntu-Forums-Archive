---
title: "Deleted ~/.eclipse, now Eclipse doesn't regenerate eclipserc"
date: 2006-06-06
forum: Programming Talk
---

### Post by atholas on 2006-06-06
I have made the mistake of deleting ~/.eclipse. I thought running eclipse again would regenerate ~/.eclipse/eclipserc, but it didn't. Is there anyway I can get eclipserc back?

**Update:**
Reading /usr/share/doc/eclipse/changelog.Debian.gz revealed that the template for eclipserc should be in the folder /usr/share/doc/eclipse-platform/examples/, but it isn't on Ubuntu. A little bit of goolging revealed an unsecured machine with eclipserc (in the path above). Just in case if someone else also run into the same problem, here is eclipserc:

```
# This files provides some user settings for eclipse. This is 
# usefull, when eclipse is started via menu entry. Most of this 
# settings can also be given directly on the commandline, which 
# will overwrite the settings made in this file.

# The original file can be found in 
# /usr/share/doc/eclipse-platform/examples 

# The Eclipse Workspace
# This setting is overwritten by the -data <workspace> param 
# when calling eclipse.
#
# default: $HOME/eclipse
#WORKSPACE=$HOME/eclipse

# The java to use. If this variable is already set, 
# eclipse uses this setting. Uncomment to set JAVA_HOME 
# to a different location. Passing '-vm <JVM> as an argument will
# overwrite it. If JAVA_HOME isn't set at all, and no 
# '-vm <JVM>' argument is passed to eclipse, /usr/bin/java 
# will be used.
#
#JAVA_HOME=/usr/local/jsdk1.4

# This is appended after every other given argument to be passed 
# directly to the Java Virtual Maschine.
# Every argument to the virtual maschine is useable, especially 
# -Xmx<RAM> should be set to something usefull like -Xmx256M. Other 
# options have to be seperated by spaces.
# The variable content MUST NOT start with -vmargs, this is included
# by the eclipse startscript. 
#
# This setting is overwritten by the -vmargs param. 
#
# Default: not set
#VMARGS="-Xmx256M"

# Disable/enable GTK AntiAlising for eclipse. Disabling AA speeds
# up eclipse on some computers. You probably want to change the 
# eclipse fonts to TT ones to get the same readability.
#
# This will supersede the normal GTK environment variable.
#
# GTK_USE_XFT=(0|1) (off|on)
# Default: not set.
#GTK_USE_XFT=0

# Linked in eclipse dirs.
# This setting can be used to link a dir with additionaly 
# features/plugins in. See 
# /usr/share/doc/eclipse-platform/README.Debian for more information
# on this freature.
# 
# Please note, that the $HOME/.eclipse/user.links file is already
# included by the startscript.
#
# LINKS=<URL to a *.links file>
# Default: not set
#LINKS=$HOME/.eclipse/more_user.links

# Debugging switch:
# Set to the path, where your .option file is. If set, eclipse is 
# also started with "-consolelog", which mirrors the error log 
# to the console.
# A sample .options is included at ~/.eclipse/debug_options
#
# This setting is overwriten by the -debug param. You also
# need to supply the -consolelog param then.
#
# Default: not set -> eclipse not started in debugmode
#DEBUG_OPTIONS=$HOME/.eclipse/debug_options

# The GUI Toolkit to be used.
# Two toolkits come with eclipse itself: gtk and motif. Additional 
# toolkits may become avavilable with additionl packages!
# If the specified toolkit can't be found, eclipse will not start!
#
# This setting is overwritten by the -ws <toolkit> param.
# WS=-ws (gtk|motif)
# default: the toolkit chosen by the update-alternative system
#WS="-ws gtk"

# Set to off to disables the Splash Screen. Do that if you 
# use a different toolkit than gtk and can't stand the gtk windows. 
#
# Default: not set -> splash screen shown.
#SPLASH=off


```

---

### Post by googatrix on 2009-07-18
Thanks, this is really helpful.

---

