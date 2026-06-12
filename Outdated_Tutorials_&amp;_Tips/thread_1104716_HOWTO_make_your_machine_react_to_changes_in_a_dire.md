---
title: "HOWTO: make your machine react to changes in a directory"
date: 2009-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by unutbu on 2009-03-23
**[SIZE="4"]Examples of who might find this useful:[/SIZE]**
[list]
[*]People who want to backup a directory every time a file in that directory is modified
[*]Groups of people who want to share a directory and need the ownership and permission of all files set so everyone can share the files.
[*]Programmers who want their source code recompiled every time a change is made
[*]LaTeX authors who want their .tex file(s) processed every time a change is made
[*]Photographers who want to drop images into a directory and have them automatically resized
[*]YouTube users who want the videos they watch to be automatically saved to a directory
[/list]

[B][SIZE="4"]
Summary:[/SIZE][/B]
dirmon.py is a small python script meant to run in the background or at startup, which can monitor a directory (and all its subdirectories) for changes. It can be configured to run arbitrary commands every time a file or subdirectory is created or modified. 

There are three components to setting up dirmon: the dirmon.py program, a configuration file (~/.dirmon), and a script to be run whenever a file is created or modified.

Below you will find Instructions on how to setup each of these components.
Following the Instructions is an Examples section which shows configuration files and scripts for each of the situations listed above.

[B][SIZE="4"]
The instructions:[/SIZE][/B]
[list]
[*]Install the python-pyinotify package (~260 KiB)
```
sudo apt-get install python-pyinotify
```
[*]Save this to ~/bin/dirmon.py.
[php]
#!/usr/bin/env python
import os
import optparse
from pprint import pformat
from pyinotify import (WatchManager, Notifier, ProcessEvent,
                       ALL_EVENTS,IN_MOVED_TO,IN_MOVED_FROM,IN_DELETE,IN_MODIFY,
                       IN_CREATE)
from subprocess import Popen,PIPE,STDOUT
import signal
import re

__author__ = 'unutbu'
__version__ = '$Revision: 0.2 $'
__date__ = '$Date: 2009-03-23 $'
__notes__='''
This causes dirmon.py to reread the configuration file:
kill -SIGUSR1 $(ps axuw | awk '/[d]irmon/{print $2}')
'''
__usage__='''
dirmon.py
'''

class MyProcessEvent(ProcessEvent):
    def __init__(self,config):
        self.config=config
        self.pat=re.compile(config['filter'])
    def path(self,event):
        return event.name and os.path.join(event.path, event.name) or event.path
    def cmd(self,event):
        path=self.path(event)
        cmd=self.config['command'].replace('{}',path)
        return cmd
    def process_default(self,event):       
        path=self.path(event)
        if self.pat.search(path):
            proc=Popen(self.cmd(event), shell=True, stdout=PIPE, )
            output=proc.communicate()[0]
            print output,

class ConfigProcessEvent(ProcessEvent):
    def __init__(self,main):
        self.main=main
    def process_default(self,event):
        outfile=os.path.join(self.main.opt.config_file+'.out')
        fh=open(outfile,'w')
        fh.write('Rereading %s'%self.main.opt.config_file)
        fh.close()
        self.main.read_config_file()
        self.main.setup_watch_manager()

class Main(object):
    def parse_options(self):
        usage = 'usage: %prog [options]'
        parser = optparse.OptionParser(usage=usage)
        parser.add_option('-c', '--config-file', dest='config_file', 
                          default=os.path.join(os.environ['HOME'],'.dirmon/dirmonrc'),
                          help='specify config-file. Default=~/.dirmon', 
                          metavar='FILE')
        parser.add_option('-v', '--verbose', dest='verbose',
                  action='store_true', 
                  default=False,
                  help="print messages to stdout")
        (self.opt, self.args) = parser.parse_args()

    def read_config_file(self):
        if os.path.exists(self.opt.config_file):
            self.config_dir,filename=os.path.split(self.opt.config_file)
            fh=open(self.opt.config_file,'r')
            self.stanzas=[]
            config={}
            for line in fh:
                if line.startswith('#') or len(line.strip())==0:
                    continue
                elif line.startswith('path:'):
                    config['path']=os.path.expanduser(line.replace('path:','').strip())
                    #
                    # If the path does not end with a slash (/), the WatchManager
                    # does not recursively monitory subdirectories.
                    #
                    if os.path.isdir(config['path']) and not config['path'].endswith('/'):
                        config['path']=config['path']+'/'
                elif line.startswith('event:'):
                    config['event']=line.replace('event:','').strip()
                elif line.startswith('command:'):
                    config['command']=os.path.expanduser(
                        line.replace('command:','').strip())
                elif line.startswith('filter:'):
                    config['filter']=line.replace('filter:','').strip()
                if (('path' in config) and ('event' in config) and
                    ('filter' in config) and ('command' in config)):
                    self.stanzas.append(config)
                    config={}
            if self.opt.verbose:
                print(pformat(self.stanzas))
        else:
            print "Error: can't find config file %s"%self.opt.config_file
            exit(1)

    def setup_watch_manager(self):
        wm = WatchManager()
        self.notifier = Notifier(wm)
        #
        # Monitory your own config file (.dirmon)
        #
        mask = IN_MODIFY|IN_CREATE
        wm.add_watch(self.config_dir, mask, proc_fun=ConfigProcessEvent(self))
        for config in self.stanzas:
            if config['event']=='file_created':
                mask = IN_CREATE
                wm.add_watch(config['path'], mask, rec=True, auto_add=True,
                             proc_fun=MyProcessEvent(config))
            elif config['event']=='file_modified':
                mask = IN_MODIFY|IN_CREATE
                wm.add_watch(config['path'], mask, rec=True, auto_add=True,
                             proc_fun=MyProcessEvent(config))
            elif config['event']=='dir_changed':
                mask = (IN_MODIFY|IN_CREATE|
                        IN_DELETE|IN_MOVED_FROM|
                        IN_MOVED_TO)
                wm.add_watch(config['path'], mask, rec=True, auto_add=True,
                             proc_fun=MyProcessEvent(config))
            elif config['event']=='paranoid':
                mask = ALL_EVENTS
                wm.add_watch(config['path'], mask, rec=True, auto_add=True,
                             proc_fun=ProcessEvent())

    def sigusr_handler(self,signal, frame):
        raise UserWarning
        
    def setup_sigusr_handler(self):
        signal.signal(signal.SIGUSR1, self.sigusr_handler)

    def loop(self):
        while True:  
            try:
                self.notifier.process_events()
                if self.notifier.check_events():
                    self.notifier.read_events()
            except KeyboardInterrupt:
                self.notifier.stop()
                break
            except UserWarning:
                self.read_config_file()
                self.setup_watch_manager()

    def __init__(self):
        self.parse_options()
        self.read_config_file()
        self.setup_watch_manager()
        self.setup_sigusr_handler()
        self.loop()

if __name__=='__main__':
    Main()



[/php]
[*]Make the program executable:
```

chmod 755 ~/bin/dirmon.py
```

[*]dirmon.py is going to monitor a directory. Each time a file changes in that directory, a script is going to be run. For example, save this script in ~/bin/dirmon-script.sh
[PHP]
#!/bin/sh
echo "File modified: $1"[/PHP]

You can put any commands that you wish here. 
"$1" will hold the name of the file that has changed.

Make the script executable:
```

chmod 755 ~/bin/dirmon-script.sh
```

[*]Next we make a configuration file. Using a text editor, save the following in ~/.dirmon.
```
  
path: /path/to/directory
event: file_modified
command: ~/bin/dirmon-script.sh
filter: regexp
```

Change /path/to/directory to the directory you wish to monitor.
Change ~/bin/dirmon-script.sh to the path to your script.
regexp can be any (python) regular expression. Only files whose name matches the regexp pattern will activate the script. If you want all files in the directory to activate the script (when a change is made), you can use a single period (.) as your regexp. 

[*]*(You can skip this section the first time through and come back to this once you get a taste for what's going on...)*
Fun facts about the configuration file .dirmon: 
[list]
[*]In the command specified after the "command:" keyword, every occurrence of paired-braces {} will be replaced by the name of the file which triggered dirmon.py. 

[*]The regexp is matched against a full path name, not just a filename. Keep this in mind if you use ^ to match the beginning of a string. You will be matching the beginning of the full path, not the beginning of the filename.

[*]WARNING: If your script writes output into the monitored directory, you must make sure the filter pattern excludes that output, lest dirmon.py end up in an infinite loop... highly undesirable.

[*]Collectively, a path,event,command and filter statement comprise a stanza. You can monitor more than one directory simply by writing a stanza for each directory you wish to monitor. No two stanzas can have the same path. If you do, only the last such stanza will have an effect. If you run into this situation, simply modify your script to contain the commands from both stanzas.

[*]Lines that begin with # or which contain only spaces are ignored

[*]If you want a command to be run only when a file is created (rather than when it is modified), use
```

event: file_created
```

When you use 
```

event: file_modified
```

the command will be run whenever a file is created or modified.

[/list]

[*]To monitor the directory, run
```
dirmon.py &

```
Fun facts about dirmon.py:
[list]
[*]dirmon.py reads the configuration file ~/.dirmon by default. If you wish it to read a different configuration file, run
```
dirmon.py --config-file /path/to/config/file
```
[*]You can ask dirmon.py to reread the configuration file after it has been started.
Just edit ~/.dirmon and then send dirmon.py a SIGUSR1 signal:
```

kill -SIGUSR1 $(ps axuw | awk '/[d]irmon/{print $2}')
```
[*]If you run ```

dirmon.py --verbose
```
It will print out a list of configuration stanzas that it is currently using.
This might be useful for debugging problems.
[/list]
[/list]
[B][SIZE="4"]
Examples:[/SIZE][/B]
[list]
[*]For people who want to backup a directory:
Place in ~/bin/dirmon-script.sh:
[PHP]#!/bin/sh
rsync -a --delete /path/to/source/ /path/to/target/
[/PHP]
Place in ~/.dirmon:```

path: /path/to/source/
event: dir_changed
command: ~/bin/dirmon-script.sh
filter: .

```
[*]For groups of people who want to share a directory:
Place in ~/bin/dirmon-script.sh:
[PHP]#!/bin/sh
dir=$(dirname "$1")
chown users:users -R "$dir" 
chmod g+rw "$1"[/PHP]

Place in ~/.dirmon:
```
path: /path/to/shared/directory
event: file_modified
command: ~/bin/dirmon-script.sh {}
filter: .
```


[*]For programmers who want their source code recompiled every time a change is made:
Place in ~/bin/dirmon-script.sh:
[PHP]#!/bin/sh
dir=/path/to/project/source
cd "$dir"
make[/PHP]

Place in ~/.dirmon:
```
path: /path/to/project/source
event: file_modified
command: ~/bin/dirmon-script.sh
filter: \.c$
```

[*]LaTeX authors who want their .tex file(s) processed every time a change is made
Place in ~/bin/dirmon-script.sh:
[PHP]#!/bin/sh
latex $1[/PHP]

Place in ~/.dirmon:
```
path: /path/to/document/
event: file_modified
command: ~/bin/dirmon-script.sh {}
filter: \.tex$

```
[*]Photographers who want to drop images into ~/images_in and have them resized to 800x600 and placed in ~/images_out:
Install the imagemagick package:
```
sudo apt-get install imagemagick
```
Place in ~/bin/dirmon-script.py:
[php]
#!/usr/bin/env python
import os
import sys

target_dir=os.path.join(os.environ['HOME'],'images_out')
try:
    os.makedirs(target_dir)
except OSError:
    pass
source=sys.argv[1]
filename=os.path.split(source)[1]
target=os.path.join(target_dir,filename)
cmd='convert -resize 800x600! %s %s'%(source,target)
print cmd
os.system(cmd)
# os.unlink(source)  # Uncomment this line if you wish to delete files in ~/images_in after being resized.
[/php]

Place in ~/.dirmon:
```
path: ~/images_in
event: file_modified
command: ~/bin/dirmon-script.py {}
filter: \.tex$
```

[*]YouTube users who want every video they watch to be automatically saved to ~/Videos
Place in ~/bin/dirmon-script.sh:
[PHP]#!/bin/sh
rsync -a /tmp/Flash* ~/Videos[/PHP]

Place in ~/.dirmon:
```
path: /tmp
event: file_modified
command: ~/bin/dirmon-script.sh
filter: Flash
```
[/list]

I hope you have as much fun using dirmon as I had writing it. Enjoy. :popcorn:

---

### Post by binbash on 2009-03-24
Deleted Grysnc, one of the best tutorials on this forum! Thanks

---

### Post by atlas95 on 2009-03-24
Hi,
Very good howto, I have discover the last week INCRONTAB this do the same thing no ? I will try your python script tonigh

---

### Post by lukjad on 2009-03-24
Niiiiice! 8) This looks really useful. Thanks!

---

### Post by unutbu on 2009-03-24
Hi atlas95, both dirmon.py and crontab can be configured to run scripts.

Here is how I would summarize the difference:
dirmon scripts get run whenever a file changes in a directory.
crontab scripts get run based on the current time or date.

@binbash and lukjad007: Thanks very much for the nice comments! :)

---

### Post by JohnFH on 2009-03-25
> **unutbu said:**
> Hi atlas95, both dirmon.py and crontab can be configured to run scripts.

Here is how I would summarize the difference:
dirmon scripts get run whenever a file changes in a directory.
crontab scripts get run based on the current time or date.


Yes that's right, but he was talking about incron not cron.  incron = inotify cron, and does the job nicely.  See incrond( 8 ):

"The inotify cron daemon (incrond) is a daemon which monitors filesystem events and executes commands defined in system and user tables."

incron works well and I've used it in the past to keep directories in sync automatically.

---

### Post by atlas95 on 2009-03-25
JohnFH, yes, i speak about this program ;)

---

### Post by unutbu on 2009-03-25
LOL, I didn't know about incron! Thank you for bringing this to my attention, atlas95 and JohnFH. 

I've just installed incron and look forward to playing with it. Here are a few differences that pop out at me:

[list]
[*]incron implements many masks. So far, I have only implemented the IN_CREATE and IN_MODIFY masks (dirmon calls these events "file_created" and "file_modified"). It wouldn't be hard to implement other masks in dirmon. So far, I just haven't found a need.
[*]According to incrond's man page,
> 
Recursive monitoring  (whole subtrees) has not been implemented yet.

With dirmon.py you get recursive monitoring by default for free thanks to python-pyinotify.

[*]From [http://inotify.aiken.cz/](http://inotify.aiken.cz/) documentation:
> 
The incron daemon (incrond) must be run under root

dirmon.py can be run as a normal user. This might make dirmon.py a possibility for users who don't have root privileges, and can't install incron.
[*]dirmon's configuration file includes a regexp filename filter, which can allow the user-configurable script to write into a monitored directory without falling into an infinite loop. The filename filter prevents the script from being run when the filename does not match the filter. incrontab does not offer this ability. It can be mimicked by adding code to the user-defined script which does the filtering. 
[*]The incrontab configuration file does not expand ~ to the users home directory.
[*]incron automatically monitors its own configuration files. Brilliant. Why didn't I think of that? :)
[/list]

Please note that I am rather familiar with dirmon and pretty clueless about incron so the above comments only represent my first impressions and could be wrong because I do not understand incron well enough. Feel free to disabuse me of my prejudices.

---

### Post by Green_Star on 2009-03-26
Thanks for the tutorial. It is great.

I am trying to sync a 4 level tree directory. It is working great when I create/modify any file in any directory under that tree, but not syncing when I delete a file. Is this dirmon.py didn't kind when file deleted? My shell script working fine if I run manually(when file deleted), but dirmon.py not working. Can you confirm me this? 

Thanks in advance.

---

### Post by unutbu on 2009-03-27
Green_Star, you are quite right dirmon version 0.0 did not react to deleted files.
I've modified dirmon to now handle such events. You can download dirmon.py (version 0.1)
from post #1.

In your .dirmon configuration file, change
```

event: file_modified
```

to
```

event: dir_changed
```

That's it! dirmon should now react whenever a file is created, modified, deleted, or moved to or from the monitored directory.

---

### Post by Green_Star on 2009-03-27
Excellent, I just tried, working great. Thank you.


> **unutbu said:**
> Green_Star, you are quite right dirmon version 0.0 did not react to deleted files.
I've modified dirmon to now handle such events. You can download dirmon.py (version 0.1)
from post #1.

In your .dirmon configuration file, change
```

event: file_modified
```

to
```

event: dir_changed
```

That's it! dirmon should now react whenever a file is created, modified, deleted, or moved to or from the monitored directory.

---

### Post by Martje_001 on 2009-03-27
I did not read it (yet!), but it looks good, thanks!

---

### Post by HavocXphere on 2009-03-27
Nice. Bookmarked for later use.

10 respect points awarded.

---

### Post by wph on 2009-12-13
This is a very simple and elegant interface to inotify, but I do have a question:

How do I get the actual Inotify event (ie - IN_CREATE, IN_MODIFY, etc) to be passed on the command line?

I dont know Python and I have been trying to wing it, but I cant seem to capture the actual event or pass it as Argument 3 to my script.....

example cmd: dirmon.sh [dirmon.py] [EventPath] [INOTIFY EVENT]

Since I am using dir_change as the mask, I am catching the events, but I cannot seem to get which event is matched passed to my script......

Can someone mod dirmon.py so I get the event IN_CREATE, etc... passed as an argument in the cmd ? If I see an example I can do it, but it is probably simple to do - for someone with more experience with python....

TIA

WPH

---

### Post by blx_286 on 2010-02-16
Can someone point me in the right direction? I am trying to use this to backup my home directory to an external USB drive. When I run it, I get the following error:

Traceback (most recent call last):
File "./dirmon.py", line 5, in <module>
from pyinotify import (WatchManager, Notifier, ProcessEvent,
ImportError: cannot import name ALL_EVENTS

Thanks,
Tim

---

