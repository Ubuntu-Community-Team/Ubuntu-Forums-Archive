---
title: "Rsync script not working"
date: 2019-09-13
forum: New to Ubuntu
---

### Post by montfox on 2019-09-13
Hello! To test my rsync abilities with a server I set up a little script:

```
#!/bin/bash
read -p "Please indicate the path to the file on local machine: " LOCALFILE


read -p "Please indicate the path to the destination file on the server: " DESTFILE


rsync --progress -avz -e "ssh -i ~/Documents/Keys/notrealkeyname.pem" $LOCALFILE ubuntu@notrealservername:$DESTFILE

```
However, I get this after attempting to run the command

```
Please indicate the path to the file on local machine: ~/Pictures
Please indicate the path to the destination file on the server: ~/Pictures
sending incremental file list
rsync: change_dir "/home/myusername/.bin//~" failed: No such file or directory (2)


sent 20 bytes  received 12 bytes  21.33 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]

```

---

### Post by TheFu on 2019-09-13
First, setup ssh keys like this:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote

```
Test that the public key was transferred correctly:
```
ssh userid@remote
```
It should work.  If not, try  **ssh -vvvv userid@remote** and fix the errors. The "remote" must have an ssh-server running.

Then use this:
```
rsync --progress -avz  "$LOCALFILE" "userid@remote:$DESTFILE"
```

The userid must exist.
Any paths to the DESTFILE must exist.
This is a recursive sync, so really the transferred stuff should be directories, not files.
rsync has used ssh as the default transport for about 15 yrs now.

If the intent above is real, then I'd use this:
```
rsync --progress -avz      ~/Pictures     userid@remote:
```
or

```
rsync --progress -avz      ~/Pictures/      userid@remote:Pictures/
```
Note the trailing / on the source directory.  rsync cares about that a great deal.  The destination doesn't need a ~/.  It begins in the HOME of "userid" already.

There's an error about "/home/myusername/.bin//~" .  I think this is due to a mistake in the ~/.bashrc.  At the top of the .bashrc should be a check whether the script is running interactively or not.  If it isn't interactive, best to return immediately.

---

### Post by montfox on 2019-09-13
Thanks for this! ssh is working as it should, and I figured out that my script works if I have the file in my ~/.bin folder. So if I was to move ~/Pictures to ~/.bin/Pictures it would work. I took a look at my ~/.bashrc but didn't quite understand what you meant... I see the snippet of code you are speaking of, but not quite sure how to fix the [COLOR=#000000]"/home/myusername/.bin//~" error[/COLOR]

---

### Post by TheFu on 2019-09-13
> **montfox said:**
> Thanks for this! ssh is working as it should, and I figured out that my script works if I have the file in my ~/.bin folder. So if I was to move ~/Pictures to ~/.bin/Pictures it would work. I took a look at my ~/.bashrc but didn't quite understand what you meant... I see the snippet of code you are speaking of, but not quite sure how to fix the [COLOR=#000000]"/home/myusername/.bin//~" error[/COLOR]

That makes no sense - the ~/.bin/Pictures part.  These things aren't connected at all.  No way would I move ~/Pictures/ into ~/.bin/Pictures/.

I have a ~/bin/ directory which is in the PATH, so scripts in that directory can work from anywhere without specifying the full path to the script.  **echo $PATH** to see your PATH.

The ~/.bin/ error is probably in the ~/.bashrc file.  Someone who knows that file better than me might be able to help.  IDK. Regardless, they would need to see it to spot issues.

---

### Post by Skaperen on 2019-09-13
for future planning:

all you need is one simple [COLOR=#0000cd][FONT=courier new]~/.bin[/FONT][/COLOR] directory with all your scripts in there.  if you really want to have subdirectories then you will need to have all of them listed in your PATH environment variable.  another approach is to have an organization of separate subdirectories and a script to copy them into [COLOR=#0000cd][FONT=courier new]~/.bin[/FONT][/COLOR].

---

