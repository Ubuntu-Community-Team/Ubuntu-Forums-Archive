---
title: "copy file to other machines, change filename based upon extension"
date: 2015-02-06
forum: Programming Talk
---

### Post by cris7 on 2015-02-06
I'm at a total loss on how to automate this process, and not have to manually edit my script every time I need to run it.  I'm guessing maybe GREP or PED might be used, but since I don't know how to use those functions much I don't know how to even search for how to do this.

What I have to do is:[INDENT]1-update a Twinkle buddylist (file is in the format of xxxx.bud, where xxxx=4 digit extension being used by Twinkle at that machine)
2-copy that .bud file to a list of IPs in the office
[/INDENT]
[INDENT=2]-sometimes a machine may not be on the network, but I don't want to have to go in and edit the script to account for this every time I run it just to keep the script from jamming up.
[/INDENT]
[INDENT]3-when copying the .bud to the machines, it needs to read the extension name on that machine and name the .bud file to match
             -The extension can be found by looking at the .cfg file name in the directory the .bud is going into (ie. 2222.cfg).
[/INDENT]

Step one will be done manually, it's only listed here because the script will pull that file once I've edited it.  So no need to include Step 1 in the script.

An _example_ of this process might look like this:
[INDENT]I have an updated 1111.bud file on IP123.  I need to copy it to the following machines (their Twinkle extension is listed in (), .bud filename listed after in ())
[/INDENT]
[INDENT=2]IP456 (2222) (2222.bud)
IP789 (3333) (3333.bud)
IP987 (4444) (4444.bud)
IP654 (5555) (5555.bud)
IP321 (6666) (6666.bud)
[/INDENT]

Currently I have a script that I manually enter the .bud file name for each IP, looking up the information each time.  I have a long list of IPs to copy to, so this eats up a bunch of time just to update the script each time.  If I can get a script to behave like I'm looking for, I also don't have to worry about the many possible typos on the extensions as I type them in.

Any help would be greatly appreciated, both in examples and how to find stuff like this in the future.  I'm usually pretty good with web searches, but when it comes to scripting I'm still learning how to search for stuff.

---

### Post by cris7 on 2015-02-06
I hesitate to post any of the current script, just because I don't want  to create any confusion regarding my questions.  But here's a snippet of  what I currently am working with:
[INDENT]echo ""
echo ""
echo "Copying Twinkle Buddy List from ip123 at /home/USER/bin/2202.bud to all PCs in office (Ctrl-C to exit):"
#echo ""
#echo "copying to ip456"
#scp /home/USER/bin/2202.bud ip456:/home/USER/.twinkle/2222.bud
echo ""
echo "copying to ip789"
scp /home/USER/bin/2202.bud ip789:/home/USER/.twinkle/3333.bud
echo ""
echo "copying to ip987"
scp /home/USER/bin/2202.bud ip987:/home/USER/.twinkle/4444.bud 
echo ""
echo "copying to ip654"
scp /home/USER/bin/2202.bud ip654:/home/USER/.twinkle/5555.bud 
echo ""[/INDENT]

As you can see, this script needs a lot of work.  When manually editing 30+ sets of IPs and extensions it gets old, and leaves a lot of room for error.

Thanks!

---

### Post by cris7 on 2015-02-06
So basically I need a script to:

-look into the /home/USR/.twinkle/ directory of a remote machine, and grab the xxxx part of the xxxx.cfg filename
-copy zzzz.bud file from master machine into the /home/USR/.twinkle/ directory of the remote machine,
-instead of saving it as zzzz.bud on the remote machine, save it as xxxx.bug on the remote machine
-then I need it to repeat that for an entire list of remote machines, but not fail when one of those machines is not on the network

I just don't know how to tell the computer to do that...

---

### Post by ofnuts on 2015-02-06
working in a local temp directory, for each machine (**$remote**):
[LIST=1]
[*]**rm -f *.cfg** 
[*]**scp $remote:/home/USER/.twinkle/*.cfg . ** 
[*]**scp $local_master_bud $remote:/home/USER/.twinkle/$(basename *.cfg .cfg).bud ** 
[/LIST]

where:
[LIST=1]
[*]removes existing .cfg files from the local directory 
[*]gets any CFG in the remote directory (this assumes that this copy isn't a performance concern) 
[*]creates a .bud name using the root name of the.cfg ( ('basename *.cfg .cfg) and uses it in a another SCP command to copy the file to the remote. 
[/LIST]

This assumes that you get only one .CFG file. If you can get several, then you would have to iterate the local CFG files.

---

### Post by cris7 on 2015-02-06
Thanks for the thoughts ofnuts, but I DO NOT wanting ANYTHING to happen to the .cfg file on the local machines.  I only want to copy the extension from the .cfg file and use that information to name the new .bud file.

The above would cause the local Twinkle profile to be wiped out, and replaced with one from another machine.  Definitely not what I want to do.

Thanks,

---

### Post by Holger_Gehrke on 2015-02-07
> **cris7 said:**
> Thanks for the thoughts ofnuts, but I DO NOT wanting ANYTHING to happen to the .cfg file on the local machines.  I only want to copy the extension from the .cfg file and use that information to name the new .bud file.

The above would cause the local Twinkle profile to be wiped out, and replaced with one from another machine.  Definitely not what I want to do.

Thanks,

No, it it wouldn't if you did what he wrote before point 1, and do this in a **local temporary directory**. So it should be something like:
```

#!/bin/bash

# list of machines for copying
machines="ip1 ip2 ip3 ip4"

# create a new directory in /tmp and save it's name in $tempdir
tempdir=$(mktemp -d)
# pushd: bash-builtin, puts $PWD on stack and changes to the directory given as parameter
pushd $tempdir

# loop over list of machine
for remote in $machines; do
  # if ping fails, we skip this machine
  if ping -c 1 $remote ; then       
     # ... we can copy from and to it
     # copy the remote *.cfg to get it's name
     scp $remote:/home/USER/.twinkle/*.cfg .
     # copy the local .bud to the remote machine with the name of it's .cfg (cfg extension removed, bud extension appended)
     scp ~/.twinkle/*.bud $remote:/home/USER/.twinkle/$(basename *.cfg .cfg).bud  
     # we don't need the copied .cfg anymore
     rm *cfg
  fi
done

# bash-builtin, takes a dir off the top of the stack and changes to it
popd
# cleanup: remove the temporary directory (and its content)
rm -rf $tempdir

```

---

### Post by cris7 on 2015-02-09
I'm going to have to chew on that for a minute, I'm still somewhat of a novice.  Thanks for pointing out exactly which part I was misunderstanding.

I really appreciate the explanation as the code progresses, hopefully it should help me quite a bit in understanding what's going on when I finally have a chance to soak it up and run it in a test environment.

Thanks to all!

---

