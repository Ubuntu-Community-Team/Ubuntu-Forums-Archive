---
title: "Newbie need help adding progress bar to script"
date: 2015-04-01
forum: Programming Talk
---

### Post by lance bermudez on 2015-04-01
I found this script on google.com and I'm a newbie and don't know how to add it.
```

#!/usr/bin/env python3
#
#  console_progress_bar
#
#  Copyright (c) 2010-2011 Corey Goldberg (http://goldb.org)
#
#  License :: OSI Approved :: MIT License:
#      http://www.opensource.org/licenses/mit-license
#
#      Permission is hereby granted, free of charge, to any person obtaining a copy
#      of this software and associated documentation files (the "Software"), to deal
#      in the Software without restriction, including without limitation the rights
#      to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#      copies of the Software, and to permit persons to whom the Software is
#      furnished to do so, subject to the following conditions:
#
#      The above copyright notice and this permission notice shall be included in
#      all copies or substantial portions of the Software.
#
#http://code.google.com/p/corey-projects/source/browse/trunk/python3/console_progress_bar/console_progress_bar.py
#


"""
console_progress_bar.py - ascii command-line progress bar with percentage and elapsed time display


example usage:

        #!/usr/bin/env python3

        import console_progress_bar as pb

        # print a static progress bar:
        #  [##########       25%                  ]  15s/60s

        prog_bar = pb.ProgressBar(60)
        prog_bar.update_time(15)
        print(prog_bar)

        # print a dynamic updating progress bar on one line:
        #
        #  [################100%##################]  10s/10s
        #  done

        secs = 10
        prog_bar = pb.ProgressBar(secs)
        print('\nplease wait %d seconds...\n' % secs)

        # spawn asych (threads/processes/etc) code here that runs for secs.
        # the call to .animate() blocks the main thread.

        prog_bar.animate(secs)

        print('done')

"""


import sys
import time



if sys.platform.lower().startswith('win'):
    on_windows = True
else:
    on_windows = False
   
   
   
class ProgressBar:
    def __init__(self, duration):
        self.duration = duration
        self.prog_bar = '[]'
        self.fill_char = '#'
        self.width = 40
        self.__update_amount(0)
   
    def animate(self, secs):
        for i in range(secs):
            if on_windows:
                print(self, end='\r')
            else:
                print(self, (chr(27) + '[A'))
            self.update_time(i + 1)
            time.sleep(1)
        print(self)
       
    def update_time(self, elapsed_secs):
        self.__update_amount((elapsed_secs / float(self.duration)) * 100.0)
        self.prog_bar += '  %ds/%ss' % (elapsed_secs, self.duration)
       
    def __update_amount(self, new_amount):
        percent_done = int(round((new_amount / 100.0) * 100.0))
        all_full = self.width - 2
        num_hashes = int(round((percent_done / 100.0) * all_full))
        self.prog_bar = '[' + self.fill_char * num_hashes + ' ' * (all_full - num_hashes) + ']'
        pct_place = int((len(self.prog_bar) / 2) - len(str(percent_done)))
        pct_string = '%d%%' % percent_done
        self.prog_bar = self.prog_bar[0:pct_place] + \
            (pct_string + self.prog_bar[pct_place + len(pct_string):])

    def __str__(self):
        return str(self.prog_bar)
       
       
     

if __name__ == '__main__':
   
    # print a static progress bar
    #  [##########       25%                  ]  15s/60s

    p = ProgressBar(60)
    p.update_time(15)
    print('\nstatic progress bar:')
    print(p)
   
   
    # print a static progress bar
    #  [=================83%============      ]  25s/30s

    p = ProgressBar(30)
    p.fill_char = '='
    p.update_time(25)
    print('\nstatic progress bar:')
    print(p)
   
   
    # print a dynamic updating progress bar on one line:
    #
    #  [################100%##################]  10s/10s
    #  done
   
    secs = 10
    p = ProgressBar(secs)
    print('\n\ndynamic updating progress bar:')
    print('\nplease wait %d seconds...\n' % secs)
   
    # spawn asych (threads/processes/etc) code here that runs for secs.
    # the call to .animate() blocks the main thread.
   
    p.animate(secs)
   
    print('done')
   
   
   
"""
example output:


$ python3 console_progress_bar.py

static progress bar:
[##########       25%                  ]  15s/60s

static progress bar:
[=================83%============      ]  25s/30s


dynamic updating progress bar:

please wait 10 seconds...

[################100%##################]  10s/10s
done

"""

```

I want to know how do I add it to my script? I want the progress bar that looks like this
```

# print a dynamic updating progress bar on one line:
    #
    #  [################100%##################]  10s/10s
    #  done

```
I want the Progress bar to show when my script is moving the files. My code for my script with out the progess bar is.
```

#! /bin/python3.3
import subprocess
from datetime import datetime

now = datetime.now()
ntime = now.strftime("%m/%d/%Y %A %H:%M:%S")

log_file = open ('command.log', 'a', encoding="utf-8")

command_output = subprocess.check_output (['rsync','--stats','vaPh','/home/lance/Documents/','/home/lance/500gb/bin/'])

log_file.write ('\n###############################\n')
log_file.write ('#')
log_file.write (ntime)
log_file.write ('#\n')
log_file.write ('###############################\n')
#log_file.write (command_output.decode('utf-8'))
log_file.close ()

```

---

### Post by Vaphell on 2015-04-02
so how is your program supposed to know the estimated time? I doubt rsync itself can know that, i think you can only depend on the number of files to process.

Also if you are trying to perform some advanced cli voodoo, shouldn't you opt for bash which doesn't make the already tricky problem harder than necessary?

[http://www.cyberciti.biz/faq/show-progress-during-file-transfer/](http://www.cyberciti.biz/faq/show-progress-during-file-transfer/)

---

### Post by flaymond on 2015-04-05
I just use Pipeline to do that, or Zenity for more graphical. (both are bash)

---

