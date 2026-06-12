---
title: "HOWTO: Install Hellanzb - Including a working hellanzb.conf (3 Steps, no fuss)"
date: 2007-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by SilverWave on 2007-12-26
_________________________________________

**HOWTO:**

Install Hellanzb - Including a working hellanzb.conf
OS: Ubuntu 7.10
Architecture: 64bit.

About Hellanzb:
Once fully installed, all thats required is moving an nzb file to the queue directory.
The rest; fetching, par-checking, un-raring, etc. is taken care of by hellanzb.
_________________________________________

**1 -** Issue these commands:
sudo apt-get install hellanzb unrar par2 python-yenc PyPar2
sudo gedit /etc/hellanzb.conf

**2 -** Update the blank hellanzb.conf file to reflect your details (see below). 

**3 -** Issue the command:
hellanzb

Drop your nzb's to the  hellanzb/nzb/daemon.queue and hellanzb will do its thing and report on progress in the terminal.

Done :)

Cheers



Items that will need changed:
```

             username = 'gn123456',
             password = 'xyz1a2b3',

```
```

             connections = 10,

```
```

defineServer(id = 'giganews',
             hosts = [ 'news-europe.giganews.com:119' ],

```
```

Hellanzb.PREFIX_DIR = '/media/home2/hellanzb/'

```

Supply a path to the (un)rar, par2 commands and set Skip unraring to False.
```

# Supply a path to the (un)rar command
Hellanzb.UNRAR_CMD = '/usr/bin/unrar'

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = False

```

Here is my hellanzb.conf file:
```

# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 1057 2007-03-27 04:13:53Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = os.path.expanduser('~') + '/.hellanzb/log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = os.path.expanduser('~') + '/.hellanzb/log-debug'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'giganews',
             hosts = [ 'news-europe.giganews.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'gn123456',
             password = 'xyz1a2b3',
             #username = None,           # no auth
             #password = None,

             connections = 10,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = False
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s

# Important locations
# Hellanzb.PREFIX_DIR = os.path.expanduser('~') + '/.hellanzb/'
Hellanzb.PREFIX_DIR = '/media/home2/hellanzb/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'done/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True


# Maximum amount of memory used to cache encoded Article data segments.
# hellanzb will write article data to disk when this cache is exceeded
# Available settings:
# -1: Unlimited size
#  0: Disable cache (only cache to disk)
# >0: Limit cache to this size, in bytes, KB, MB, e.g.:
#     1024 '1024KB' '100MB' '1GB'
#Hellanzb.CACHE_LIMIT = 0


# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
Hellanzb.UNRAR_CMD = '/usr/bin/unrar'

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = False

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Enable libNotify Daemon notifications
Hellanzb.LIBNOTIFY_NOTIFY = False


# Disable ANSI color codes in the main screen (preserves the in place scroller)
#Hellanzb.DISABLE_COLORS = False

# Disable ALL ANSI color codes in the main screen (for terminals that don't
# support ANY ANSI codes
#Hellanzb.DISABLE_ANSI = False


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# IP address on which the XMLRPC Server will be binded to.
# Type '0.0.0.0' for any interfaces, '127.0.0.1' will disable remote access
Hellanzb.XMLRPC_SERVER_BIND = '127.0.0.1'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to http://www.newzbin.com for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'

```
The hellanzb.conf above contains MY data so it will need to be changed to reflect your details.
You have, as far as practical, a working copy - obviously the pw has been changed :P



_________________________________________

Notes:

python-yenc is optional but recommended for speed.
PyPar2 is an optional gui for par2, Hellanzb does the par checking for you so it should never be needed but I like to be prepared ;)



_________________________________________

Extras:

I have set Firefox to download nzb files to: hellanzb/nzb/daemon.queue
hellanzb/done is where your finished downloads are placed



_________________________________________

Acknowledgments:

This how to is based on various Google searches and the following posts:
[http://www.hellanzb.com/](http://www.hellanzb.com/)
[http://ubuntuforums.org/archive/index.php/t-462163.html](http://ubuntuforums.org/archive/index.php/t-462163.html)
[http://lunapark6.com/hellanzb-automated-nzb-downloader-and-more.html](http://lunapark6.com/hellanzb-automated-nzb-downloader-and-more.html)

Best of Luck :)

---

### Post by nfox on 2008-01-06
Hey, what does this line mean in the config file:

  #bindTo = '204.31.33.7',    # connect FROM this ip address

I know what it says, but why would I ever want to use this? Like, Apache has a bind-to and so does SAMBA and I get why you want to bind a web server but where does it apply to Hellanzb? Is this for a web interface or something?

Just wondering...

---

### Post by SilverWave on 2008-01-07
I was thinking that bindTo would allow you to choose which of your nic's to use (if you had more than one) but tbh I don't know ;)

I have had a look at the homepage and the search returns these hits:
[http://www.hellanzb.com/trac/hellanzb/search?q=bindTo&wiki=on&changeset=on&ticket=on](http://www.hellanzb.com/trac/hellanzb/search?q=bindTo&wiki=on&changeset=on&ticket=on)

bindTo has previously had a patch applied to address a problem...

[http://www.hellanzb.com/trac/hellanzb/attachment/ticket/204/fixbindto.patch](http://www.hellanzb.com/trac/hellanzb/attachment/ticket/204/fixbindto.patch)

... so it does still have a function :)

Checking the example IP ...
[http://ws.arin.net/whois/?queryinput=204.31.33.7](http://ws.arin.net/whois/?queryinput=204.31.33.7)

Returns this:

> OrgName:    ICG NetAhead, Inc. 
OrgID:      ICGN
Address:    1025 Eldorado Blvd.
City:       Broomfield
StateProv:  CO
PostalCode: 80021
Country:    US
NetRange:   204.31.16.0 - 204.31.79.255

If you do confirm what bindTo does please return and post an update :D

---

### Post by nfox on 2008-01-10
Yea, the NIC thing was a good idea.

 I think it may be related to the web-based UI. I know I wouldn't want someone in pick-a-place to access my usenet account and download bad stuff. 

Still a little odd though

---

### Post by hoverX on 2008-07-22
ok i've installed hellanzb but i cannot find a directory called daemon.queue.  What is the exact path of this directory?

---

### Post by darco on 2008-07-23
> **hoverX said:**
> ok i've installed hellanzb but i cannot find a directory called daemon.queue.  What is the exact path of this directory?

it  depends what you entered in the .conf file for this line

Hellanzb.PREFIX_DIR = '/media/home2/hellanzb/'

then just drill down to find the folder

darco

---

### Post by nfox on 2008-07-23
the queue folder is as stated above. mine is specifically here:

~/.hellanzb/nzb/daemon.queue

using default options to install which is where I'm guessing yours is.

---

### Post by Dodominyk on 2008-07-26
Thanks for the guide.

How do you set Firefox to download nzb files to hellanzb/nzb/daemon.queue. I can only get Firefox to always download nzb files, but I have to enter the location every times.

---

### Post by darco on 2008-07-28
Strange but I have been using Hella for a long time now and today after I d/l an .nzb, everything looks fine. Hella reports "found new nzb", "Parsing", then "parsed" then Hella says its "queued" and nothing downloads? I have tried several .nzbs and they all just sit there? Any clue?

darco

---

### Post by Drizzel on 2008-08-08
Hi, I followed your tut to the T and hellanzb refuses to connect. I have to use lottanzb in standalone mode to be able to download anything. I compared my hellanzb.conf file to yours and did everything just like yours. Why wont hellanzb connect. I would like to use it instead of having to use lottanzb in standalone mode. Tons of people use hellanzb, why wont it work for me? I have read countless tutorials on getting hellanzb to work and not once has it connected. Very dissappointing.

---

### Post by nfox on 2008-08-08
Dodominyk, 
that's not a hellanzb thing but as I find firefox's d/l memory to be a bit flaky, I rely on downthemall since it is so convenient. unless of course you change hella's conf to point to your desktop as the queue directory.

darco and Drizzel, 
what are your setups? you followed the guide to a T but there could be other factors. I hate to ask you to double check your username/password but there's not much we can go off of. 
As far as I've seen from my lil' slipups with the first installation I did with it, there is no real debugging you can do directly to see why. For example, if the folder isn't writable for whatever reason it will queue or if your user/pass combo is wrong then it will show the same. make sure you can ping the server and all. Maybe another usenet service would let you narrow down whether you can even log into the server before assuming it's your computer. 
Post your conf files and are you running other services that might interfere?

---

### Post by Drizzel on 2008-08-09
Yeah I went over it again and again trying to track down the problem for about 5 hrs yesterday. There's no reason it shouldnt work. I've actually been trying to get hellanzb installed and working for a couple of months now. Its ridiculous really. I'm done with Hella. I"ve gone back to using altbinz through wine. Thx for replying though. :)

---

### Post by romeyde on 2008-08-10
See any issues here?   Hellanzb works fine for me but I have an ongoing problem that I've been dealing with ages now and it's starting to get annoying...   Anytime I reboot,  Hellanzb automatically starts but I always have to kill the process and then restart it using sudo,  ie,   sudo /etc/init.d/hellanzb start.    Then after I do that, it works as expected, if I don't do that, it ignores any download requests...   This is what my startup file looks like, see any issues here?   Always thought it was some sort of permission issue but if I restart it with sudo, wouldn't that be the same?


cat /etc/init.d/hellanzb 

#!/bin/bash
#
# hellanzb       Start the hellanzb.
#


NAME=hellanzb

trap "" 1
export LANG=C

case "$1" in
  start)
    echo -ne "Starting $NAME"
    /usr/bin/screen -S $NAME -d -m /usr/bin/hellanzb > /dev/null 2> /dev/null
    echo "."
    ;;
.
.
.

---

### Post by nfox on 2008-08-11
Below is the default conf file. I don't see the part you posted though. Do not run (most any) this program with sudo... 

There is something, like your home folder, that has the wrong permissions as far as I can tell.

/etc/hellanzb.conf has the main directory which usually is ~/.hellanzb/nzb/ which you should be able to access.



******************************************************************************
```

# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 1057 2007-03-27 04:13:53Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = os.path.expanduser('~') + '/.hellanzb/log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = os.path.expanduser('~') + '/.hellanzb/log-debug'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'changeme',
             hosts = [ 'news.changeme.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'changeme',
             password = 'hella',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = False
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = os.path.expanduser('~') + '/.hellanzb/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'done/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True


# Maximum amount of memory used to cache encoded Article data segments.
# hellanzb will write article data to disk when this cache is exceeded
# Available settings:
# -1: Unlimited size
#  0: Disable cache (only cache to disk)
# >0: Limit cache to this size, in bytes, KB, MB, e.g.:
#     1024 '1024KB' '100MB' '1GB'
#Hellanzb.CACHE_LIMIT = 0


# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = True

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Enable libNotify Daemon notifications
Hellanzb.LIBNOTIFY_NOTIFY = False


# Disable ANSI color codes in the main screen (preserves the in place scroller)
#Hellanzb.DISABLE_COLORS = False

# Disable ALL ANSI color codes in the main screen (for terminals that don't
# support ANY ANSI codes
#Hellanzb.DISABLE_ANSI = False


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# IP address on which the XMLRPC Server will be binded to.
# Type '0.0.0.0' for any interfaces, '127.0.0.1' will disable remote access
Hellanzb.XMLRPC_SERVER_BIND = '127.0.0.1'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to http://www.newzbin.com for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'

```

---

### Post by romeyde on 2008-08-11
> **nfox said:**
> Below is the default conf file. I don't see the part you posted though. Do not run (most any) this program with sudo... 

There is something, like your home folder, that has the wrong permissions as far as I can tell.

/etc/hellanzb.conf has the main directory which usually is ~/.hellanzb/nzb/ which you should be able to access.

I'm guessing it's because the program is starting up on boot via init.d and running as root.   I kill it and restart it using sudo but then it still has my permissions/environment?

Just guessing here...  But when started as root on boot it for some reason is having issues accessing these files in my home dir and then it's all good when I restart it with sudo?

drwxrwxrwx  2 root    root    4096 2008-08-10 23:47 daemon.working
-rw-rw-rw-  1 root    root      55 2008-08-10 23:47 hellanzbState.xml

The rest of the files n dirs in the nzb directory belong to my userid.

Make sense?   

How do I start the daemon as me instead of root via init.d?

Would I change this in the /etc/init.d/hellanzb script

/usr/bin/screen -S $NAME -d -m /usr/bin/hellanzb > /dev/null 2> /dev/null

to something like this?

/usr/bin/sudo -u <USERNAME> /usr/bin/screen -S $NAME -d -m /usr/bin/hellanzb > /dev/null 2> /dev/null

if so, that the right place or should sudo go after screen?   like this?

/usr/bin/screen -S $NAME -d -m /usr/bin/sudo -u <USERNAME> /usr/bin/hellanzb > /dev/null 2> /dev/null


(sorry for all the questions) :)

---

### Post by nfox on 2008-08-12
Now I'm not sure what you're real issue is but all I know is that hellanzb doesn't run unless it's in /etc/init.d/ and then I just type hellanzb into a terminal and it polls the queue. If you're lookinig to skip the terminal part, put a .desktop launcher in your autostart folder for your WM and tell it to run in a terminal and leave the terminal open after the script ends.
Then a terminal will popup on login and have hellanzb reading the queue right?

---

### Post by robert114 on 2008-08-14
Hi to automatic load Hellanzb I've tried a upstart script See below. You can put the code in a (new) upstart file, for example '/etc/event.d/hellanzb'. Without making the file executable, you can start the upstart event with the 'start hellanzb' command. If you reboot your system Hellanzb will get started.

[PHP]start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
stop on shutdown
respawn
exec hellanzb[/PHP]

But of course there is a downside... it won't unrar! And i don't understand why!?!

So maybe I help you folks maybe not.

---

### Post by robert114 on 2008-08-14
Here is how i 'fixed' it. It's not quite the 'legal' way to do it, but it does the trick to me.

First, I still don't know why unrar doesn't work with upstart but i've made a script to start Hellanzb and i called that script '/home/robert/hellanzb' this script gets called by the upstart job hellanzb as described above in my previous message but i call the script in my home directory in the pre-start section of the start-up job.

```
start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
stop on shutdown
respawn

pre-start script
    # prepare environment
    /home/robert/hellanzb      
end script

exec blablablathisdoesntdoanything
```


goodluck

---

### Post by heiNey on 2008-12-09
is there any way to make hellanzb shut the computer down when the queue is empty?

---

### Post by antrozous812 on 2009-12-18
Thank you for this simple yet efficient tutorial... I had to try a couple of others before finding yours. 
Now, I'm glad it works, thanks to you.

You said in your tutorial, that you configured Firefox to download/save nzb files to the queue folder; how did you manage to do this? 

Thanks. 

-C.

---

### Post by hypnoticstate on 2009-12-19
I'm a serial newsgroup leecher and tbh just type the following

sudo apt-get install klibido

job done

---

