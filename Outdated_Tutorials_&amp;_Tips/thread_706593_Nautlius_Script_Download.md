---
title: "Nautlius Script: Download"
date: 2008-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by motin on 2008-02-24
I often find it quicker and more reliable to use wget to download files from the web. This script simplifies this process. 

Features optional automatic installation of dependencies, zenity progress dialogues and a simple URL validity check.

For usage, read the comments in the script:

```
#!/bin/bash
#Title=Download URL in clipboard to this directory
#Title[se]=Ladda ner länk i urklipp hit
# 
# Download URL in clipboard to this directory
#
# Installation:
# Put this script into the Nautilus script dir (~/.gnome2/nautilus-scripts) and make it executable.
# You will need the packages "wget" and "xclip" installed:
# sudo apt-get install wget xclip
#
# Usage:
# Right-click on files in Nautilus and choose Scripts -> Download URL in clipboard to this directory
#
# Acknowledements and version history:
# v20080224 - Fredrik Wollsén
#
# License GPL v3
#
# Feel free to provide feedback on this script here:
# http://ubuntuforums.org/showthread.php?t=
#
# THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR
# IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
# WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
# DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE
# GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER
# IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
# OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN
# IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

# Always make sure that zenity is available
if [ ! -x /usr/bin/zenity ] ; then
	xterm -e "echo 'To continue with this script, we need a certain package for nice dialogues (zenity). Press Enter to automatically install it. Press Ctrl+C to abort.' && read DUMMY && gksudo -- apt-get install zenity && echo && echo 'If no errors occured, you should now have zenity installed. This window will close in 4 seconds...' && sleep 4";
	if [ ! -x /usr/bin/zenity ] ; then
		exit 1;
	fi	
fi

# Make sure we are running in X
if [ ! -n "$DISPLAY" ] ; then
	zenity --error --text='The DISPLAY variable is not set correctly - cannot continue...'
	exit 1;
fi

# Make sure wget and xclip is available
if [ ! -x /usr/bin/xclip ] ; then
	zenity --question --text "You will need the packages 'wget' and 'xclip' installed in order to use this script. Do you want to install these right now?"
	INSTALL_XCLIP=$?
	if [ "$INSTALL_XCLIP" == 0 ] ; then
		xterm -e "gksudo -- apt-get install wget xclip && echo 'If no errors occured, you should now be all set! This window will close in 4 seconds...' && sleep 4"
	else
		exit 1;
	fi
fi

# Get URL from clipboard
URL=`xclip -o`;

# Make sure we have at least some kind of valid url
URL_TEST=`echo $URL  | grep '://'`
if [ "$URL_TEST" == "" ] ; then
	zenity --error --text="Sorry but \"$URL\" is not a valid URL. (Couldn't find any '://' in it...)"
	exit 1;
fi

# Download to current directory, using zenity to show a progress bar and download rate (Thanks Twigman from http://ubuntuforums.org/showthread.php?t=306515 !)
cd dirname $0
wget "$URL" 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --progress --title="Downloading File..."

exit 0;
```

---

