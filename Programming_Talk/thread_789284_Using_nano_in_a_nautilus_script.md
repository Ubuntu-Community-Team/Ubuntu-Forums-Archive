---
title: "Using nano in a nautilus script"
date: 2008-05-10
forum: Programming Talk
---

### Post by NormR2 on 2008-05-10
Can nano be used in a (GNOME) nautilus script?  Is there a list of what programs can be used in nautilus scripts?

I have a two line script:
#!/bin/sh
nano $1 >> ~/nano_results
 that is called by nautilus, but nano isn't started.  I get a blank line in nano_results for each attempt.

I'd like to use it to remove the Windows x'0D' characters on a bunch of batch files I'm converting.  I prefer the GUI environment
to the commandline when there a large number of long named files I want to edit. Or is there an easy way in commandline/terminal mode to select a file and issue a command passing the filename to a program?

Thanks,
Norm

---

### Post by dougfractal on 2008-05-10
Hi

I use sed  or tr to change files


cat infile | tr  "\n" " " > outfile   #  change \n to space

sed -i -e "s/\n/ /g"  inoutfile   #  change \n to space


good luck

---

### Post by NormR2 on 2008-05-10
Just entered a script and it does the job!!!  Removes the x"0d" from the file.  Much better than nano.

#!/bin/sh/
sed -i -e "s/\r//g" $1

But that still leaves the question:
Why didn't nano work? Why wasn't it started from the script?

Thanks,
Norm

---

### Post by dougfractal on 2008-05-10
> **NormR2 said:**
> Can nano be used in a (GNOME) nautilus script?  Is there a list of what programs can be used in nautilus scripts?



I'm not sure what you mean.

A Launcher script that you can drag a file onto to open?

You might have to launch a terminal shell before starting nano.  

What sort of things to be in the nano_results. the error log?

---

### Post by NormR2 on 2008-05-10
If I create a script:

#!/bin/sh
nano $1 >> ~/nano_results

and put that script in the nautilus-scripts folder, I see an entry in the context menu I get when I right-click on a file while in the nautilus File-browser. If I choose nano entry, I the script to executes (the file nano_results is created), BUT the nano program doesn't appear to open/start execution.
I have several other scripts in the same folder and am able to select them and have them execute as I expect. One uses the java command, another gedit. 
Is there something different about nano and/or nautilus that keeps nano from executing from a script when invoked from nautilus?

Norm

---

### Post by dougfractal on 2008-05-11
> **NormR2 said:**
> If I create a script:

#!/bin/sh
nano $1 >> ~/nano_results

and put that script in the nautilus-scripts folder, I see an entry in the context menu I get when I right-click on a file while in the nautilus File-browser. If I choose nano entry, I the script to executes (the file nano_results is created), BUT the nano program doesn't appear to open/start execution.
I have several other scripts in the same folder and am able to select them and have them execute as I expect. One uses the java command, another gedit. 
Is there something different about nano and/or nautilus that keeps nano from executing from a script when invoked from nautilus?

Norm

This doesn't really answer you, because it is not passing the file name to nano, but it does open nano.


#!/bin/sh
gnome-terminal -e "nano $1 >> ~/nano_results"

---

