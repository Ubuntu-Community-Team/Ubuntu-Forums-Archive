---
title: "[HOWTO] Put a wall on your Gnome background wallpaper for receiving notifications"
date: 2009-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by baruchel on 2009-03-31
Here is how you can put on your Gnome wallpaper a wall (a kind of "facebook-like" wall with various and successive notifications being added to it while you work). You may think to it as a screenlets-like system (or some desklets-like system), but it works rather like a wall: various services (mail notifications, iCalendar events, facebook events, twitter notifications, system informations, etc.) may write on the same wall on your background. Of course, such a wall is not hidden like the other windows when you click on the hide/show button. Transparency is handled if you have some nice wallpaper behind it. Its size and position may be chosen according to your own taste. It is VERY EASY to install it and to add some new services (a new service is merely a script in any language that writes from time to time on its standard output; you don't have to care about launching it or doing anything special in order to write on the wall).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108200&stc=1&d=1238526799[/IMG]

The notifications written on the wall may use some color and basic effects (bold, underline, etc.). They may use some tiny icons taken among the Unicode characters.

A similar project is the screenlet called "Output", but huge differences do exist between the two projects: several processes can write on my "wall"; output is much nicer here; one process may run as long as it needs and write from time to time and keep its private information; etc.

[SIZE="5"]Installation[/SIZE]

The system is easy to install; you have not much to do. Just follow the explanations below.

The first thing you have to do is to install (with Synaptic) the [devilspie]("https://help.ubuntu.com/community/Devilspie") package BUT YOU DON'T HAVE TO CONFIGURE ANYTHING since the following script dynamically writes a configuration file for devilspie before using it. Really, just install the package and forget about it.

Then copy the following code in a text editor, save the file with the name desktop-console.sh and put it either with your private scripts or in /usr/local/bin. Of course you have to set its rights in order to make it executable.

The third (and last thing) is to create a profile for your gnome-terminal called **DesktopConsole** (look at the step 3 on that [page]("http://www.linuxhaxor.net/2008/05/01/configuring-linux-terminal-to-work-as-a-transparent-wallpaper-part-2/")) if you don't know about that. The most important thing is to disable the scrolling and the menubar; it is probably a good thing also to use *a smaller font* than the default one.

Under the script you will find more informations concerning the usage and the services you want to install for writing on your wall.

```
#!/bin/sh

# We look if the script is running inside the Wall
if [ "$*" = "desktop-console-daemon" ] ; then
  # We hide the cursor
  echo -n x | sed -e 's/x/\x1b[?25l/'

  # We look if ~/.desktop-console exists
  if [ ! -d ~/.desktop-console ]; then
    echo "You should create a directory called ~/.desktop-console"
    echo "and put your scripts in it."
    read pause
    exit 1
  fi
  
  cd ~/.desktop-console/
  
  # launch the scripts
  for f in *
  do
    if [ -x "$f" ] ; then
      nice -n 19 "./$f" &
    fi
  done
  wait
  read pause # in case all scripts have finished
  exit 0
fi

# We look for an existing session; in which case such a process
# is killed and the command exits
RUNNING_SESSION=`ps a | grep [d]esktop-console-daemon`
if [ $? = "0" ] ; then
  RUNNING_SESSION_PID=`echo $RUNNING_SESSION | awk '{ print $1 }'`
  echo "A previous session was detected"
  echo "Killing process $RUNNING_SESSION_PID"
  echo "You may want to run the command again"
  kill -9 $RUNNING_SESSION_PID
  exit 1
fi

# We look for an existing DektopConsole profile
gconftool-2 --dir-exists="/apps/gnome-terminal/profiles/DesktopConsole"
if [ $? != "0" ] ; then
  echo "You must define a profile from the gnome-terminal called"
  echo "    DesktopConsole"
  exit 1
fi

# We look for a geometry option
WALL_SIZE=`echo "$*" | sed 's/+.*$//'`
WALL_POS=`echo "$*" | sed 's/^[^+]*//'`
if [ "$WALL_SIZE" = "" ] ; then
  WALL_SIZE="480x320"
fi
if [ "$WALL_POS" = "" ] ; then
  WALL_POS="+16+16"
fi

# launch devilspie
TMPFILE=`mktemp` || exit 1
echo "(if (matches (window_name) \"DesktopConsole\") (begin (below) (undecorate) (skip_pager) (skip_tasklist) (wintype \"dock\") (geometry \"$WALL_SIZE\")))" >> "$TMPFILE"
devilspie "$TMPFILE" &
PID_DEVILSPIE=$!

# launch gnome-terminal
gnome-terminal --window-with-profile=DesktopConsole --hide-menubar --geometry="$WALL_POS" -x nice -n 19 "$0" desktop-console-daemon &

# wait for the process to be detected
DAEMON_DETECTED="1"
until [ $DAEMON_DETECTED = "0" ]
do
  sleep 1
  DAEMON_PROCESS=`ps a | grep [d]esktop-console-daemon`
  DAEMON_DETECTED=$?
done
kill -9 $PID_DEVILSPIE
rm -f "$TMPFILE"

```

For using the wall, just create a directory called ~/.desktop-console and put executable programs inside: when the wall will be started, these programs will be launched and whataver they may write on their standard output will be reported on the wall. [Escape sequence]("http://invisible-island.net/xterm/ctlseqs/ctlseqs.html") may be used for adding colors or effects. Below are examples.

For launching the wall, just type:
```
desktop-console.sh
```
or (with a geometry for setting the size and the position of the wall):
```
desktop-console.sh 480x360+24+24
```

Your wall should appear on the background and if you already installed some scripts in the directory ~/.desktop-console they should begin to write their notifications.

[SIZE="5"]Scripts[/SIZE]
Put your scripts in the directory ~/.desktop-console and make them executable. If you want to perform the same task on several accounts (mail, calendars, etc.); copy the scripts several time (with different names) and edit them for configuring them.

[SIZE="4"]Mail notification[/SIZE]
The following script will look for new mail at regular intervals on an IMAP server (with a SSL connection but that may be removed). It has been treid with several providers. Just copy the script in a file with whatever name you want; edit it and put the right settings inside (username, host, password); you may have several versions of it if you have several accounts.

```
#!/usr/bin/python

from time import sleep
import imaplib

host = 'imap.gmail.com'
username = 'username@gmail.com'
password = 'password'
designation = 'username@gmail.com'
delay = 300

# show at startup if no unseen message:
# set below to -1 for showing at startup and to 0 for hiding
previous_nbr = -1

while 1:
  try:
    server = imaplib.IMAP4_SSL(host,993)
    server.login(username, password)
    server.select()
    outd = server.status('Inbox','(MESSAGES UNSEEN)')[1][0].split()
    server.logout()
    new_nbr = int(outd[4][0:-1])
    if new_nbr == 0:
      out = 'No unseen message (total: ' + outd[2] + ')'
    elif new_nbr == 1:
      out = 'One unseen message (total: ' + outd[2] + ')'
    else:
      out = str(new_nbr) + ' unseen messages (total: ' + outd[2] + ')'
  except Exception,e:
    new_nbr = -2
    out = e.__str__()
  if new_nbr != previous_nbr:
    u = '\x1b[35m' + unichr(9993) + '\x1b[39m'
    print(u +' ' + '\x1b[1m' + designation + '\x1b[0m\n  ' + out)
    previous_nbr = new_nbr
  sleep(delay)

```
If the IMAP server has no SSL support, just replace the line
```
server = imaplib.IMAP4_SSL(host,993)
```
with
```
server = imaplib.IMAP4(host,143)
```
[SIZE="4"]Facebook notification[/SIZE]
The following script uses the [fbcmd]("http://www.cs.ubc.ca/~davet/fbcmd/") program; you must first install the [php5-cli]("http://packages.ubuntu.com/fr/hardy/php5-cli") package; you must then follow the instructions on the fbcmd page for configuring the tool. Then use the following script (of course you must change the path in the two lines of the script according to the exact location where you put the fbcmd tool):
```
#!/bin/sh
export FBCMD=/home/john/Scripts/fbcmd/
php /home/john/Scripts/fbcmd/fbcmd.php RECENT 3 | sed -e '/^ *$/d' -e 's/^/\x1b[34mf\x1b[39m \x1b[1m/' -e 's/    */\x1b[0m\n  /'

```
This script displays notifications once at startup and leaves. You may change its behaviour.

[SIZE="4"]iCalendar events[/SIZE]
The following script is a highly configurable script for displaying events from an iCalendar (.ics) URL. You may even use password protected online calendars (for instance the script works with private [icalx]("http://www.icalx.com/") calendars. Look at the options at the beginning of the file, and set the url, the minimal number of events to be reported on the wall, how many days have to be parsed, etc.
```
#!/usr/bin/python

import sys
import urllib2
from urlparse import urlparse
from os import path
import vobject
import cgi
import datetime

# options
url = 'http://www.hebcal.com/ical/jewish-holidays.ics'
nextValue = 1   # display AT LEAST n events
withinValue = 0 # display ALL events in the n next days
username = ''
password = ''

logo = '\x1b[32m' + unichr(8987) + '\x1b[39m'

# parsedCal: Calendrier
try:
  if len(username)>0 and len(password)>0:
    passman = urllib2.HTTPPasswordMgrWithDefaultRealm()
    passman.add_password(None, url, username, password)
    authhandler = urllib2.HTTPBasicAuthHandler(passman)
    opener = urllib2.build_opener(authhandler)
    urllib2.install_opener (opener)
  usock = urllib2.urlopen(url)
  parsedCal = vobject.readOne(usock)
  usock.close()
except Exception,e:
  print(logo +' ' + '\x1b[1miCalendar\x1b[0m\n  ' + cgi.escape(e.__str__()))
  sys.exit(1)

# calname: nom du calendrier
calname = parsedCal.getChildValue('x-wr-calname')
if not calname:
  calname = path.basename(urlparse(url).path)
if len(calname) == 0:
  calname = 'iCalendar'

# today (without the time)
today = datetime.date.today()

# mylist: liste des evenements (triee)
events = []
for e in parsedCal.vevent_list:
  if e.getChildValue('dtstart'):
    if type(e.dtstart.value) == datetime.datetime:
      e.dtstart.value = e.dtstart.value.date()
    if e.dtstart.value >= today:
      events.append(e)
events.sort(key=lambda obj: obj.dtstart.value)

for e in events:
  de = e.dtstart.value
  delay = (de - today).days
  if (nextValue > 0) or (delay <= withinValue):
    msg = de.strftime('%x')
    if delay == 0:
      msg = msg + ' (today)'
    else:
      if delay == 1:
        msg = msg + ' (tomorrow)'
      else:
        msg = msg + ' (in ' + str(delay) + ' days)'
    print(logo +' ' + '\x1b[1m' + calname + '\x1b[0m ' + msg + '\n  '
          + e.summary.value)
    nextValue = nextValue - 1
  else:
    break
    
sys.exit(0)

```

[SIZE="4"]Twitter[/SIZE]
Since I don't use Twitter I didn't spend much tome on that script, but you may extend it. Right now it displays the last status changed by a friend and leaves. It is very easy to use Twitter on the wall since usual Unix tool may interact with its API (see for instance the [page]("http://linuxbasement.com/category/topic/twitter-curl-sed")). Much can be done in a shell script with the tools curl or wget.
```
#!/usr/bin/python

import urllib2
import cgi
import sys
from xml.dom.minidom import parseString

username = 'username'
password = 'password'

try:
  passman = urllib2.HTTPPasswordMgrWithDefaultRealm()
  passman.add_password(None,
                       'http://twitter.com/statuses/friends_timeline.xml',
                       username, password)
  authhandler = urllib2.HTTPBasicAuthHandler(passman)
  opener = urllib2.build_opener(authhandler)
  urllib2.install_opener (opener)
  usock = urllib2.urlopen('http://twitter.com/statuses/friends_timeline.xml')
  data = parseString(usock.read())
  usock.close()
except Exception,e:
  print(cgi.escape(e.__str__()))
  sys.exit(1)


status = data.getElementsByTagName('status')[0]
info_date = status.getElementsByTagName('created_at')[0].firstChild.nodeValue
info_text = status.getElementsByTagName('text')[0].firstChild.nodeValue
info_name = status.getElementsByTagName('name')[0].firstChild.nodeValue
print('\x1b[36mt\x1b[39m ' + '\x1b[1m' + info_name + '\x1b[0m\n  ' + info_text)

```

---

