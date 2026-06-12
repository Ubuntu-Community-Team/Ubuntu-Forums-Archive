---
title: "[SOLVED] Openbox pipe menu in python"
date: 2008-08-31
forum: Programming Talk
---

### Post by UrbanSlayer on 2008-08-31
Hi,

I've written a small script just to list txt files from a folder as a pipemenu in Openbox, and I'm pretty certain ive got the formatting right, but when I try and use it in OB, it doesnt work at all.

This is the code:

```

#!/usr/bin/env python

import os, sys, fnmatch

class dirlist:

        def dir_contents(self, path):
                file_list=[]
                os.chdir(path)
                file_types = "*.txt"
                for fileName in os.listdir(path):
                        for ext in file_types:
                                if fnmatch.fnmatch(fileName, ext) and os.path.isdir(fileName) == False and fnmatch.fnmatch(fileName, "*.txt~") == False:
                                        file_list.append(fileName)
                return file_list

        def __init__(self, argv):
                app = "/usr/lib/kde4/bin/kate"
                default = "/usr/lib/kde4/bin/dolphin"
                list = self.dir_contents(argv[0])
                def_open = default+ " " + argv[0]
                print "<?xml version=\"1.0\" encoding=\"UTF-8\"?>"
                print "<openbox_pipe_menu>"
                print " <item label=\"%s\">" % argv[0]
                print "  <action name=\"Execute\"><execute>%s</execute></action>" % def_open
                print " </item>"
                print " <separator />"
                for fileName in list:
                        print " <item label=\"%s\">" % fileName
                        print "  <action name=\"Execute\"><execute>%s</execute></action>" % (app+ " " + os.path.join(argv[0],fileName))
                        print " </item>"

                print "</openbox_pipe_menu>"

if __name__=="__main__":
        app = dirlist(sys.argv[1:])

```


Can anyone tell me what I'm doing wrong?  Ive tested it from the cmdline and it seems to be producing the correct output, but it just shows an empty menu in OpenBox.

Thanks!

---

### Post by UrbanSlayer on 2008-08-31
Nevermind.  Turns out it was a filename within the dir causing an issue.  Grr!

---

