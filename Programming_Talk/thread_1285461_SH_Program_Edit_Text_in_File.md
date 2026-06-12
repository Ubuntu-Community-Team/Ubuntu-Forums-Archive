---
title: "SH Program Edit Text in File"
date: 2009-10-07
forum: Programming Talk
---

### Post by bengerszewski on 2009-10-07
I have a file called control in /home/skippythegoat/cydia/apps/$themename/DEBIAN

($themename being the name of whatever theme i am making) and i want the to make an sh program i can execute in the terminal that will edit it and save it.  here is what the control file looks like:

Package: com.skippythegoat.$themename
Name: Theme Name (Must be able to use spaces here)
Version: 1.0
Architecture: iphoneos-arm (wont change)
Depends: winterboard (most likely wont change)
Description: A Theme, and a very good one at that.
Homepage: [http://repo.50g.com/info/%shorterthemename.htm](http://repo.50g.com/info/%shorterthemename.htm)
Maintainer: Ben Gerszewski <skippythegoat@gmail.com> (stays the same)
Author: $authorname (needs spaces) <user@domain.com> 
Section: Themes ($section)
(must be an empty line at the end of the control file)

i have a template of this file to use, so i just need to know how to use an sh file to edit and save the things i mentioned.

Thanks in advance for your help, 

Ben

---

### Post by januzi on 2009-10-07
You could create the template with the words like:
> 
Name: THEMENAME
...
Depends: THEMEDEPENDS
Those uppercase words could be replaced by the sed
> 
#!/bin/sh
sed -e 's/THEMENAME/something/g' -e 's/XXX/yyy/g' /path/to/template > /path/to/destination
As for arguments: $0 is the script name, $1, $2 ... are the arguments from the command line

---

### Post by bengerszewski on 2009-10-07
I Have no idea what you just said...  Wouldn't there be a way to use awk to change the text?

---

