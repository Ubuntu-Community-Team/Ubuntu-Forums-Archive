---
title: "Howto: Automounting sshfs (and possibly other network shares)"
date: 2007-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Darwin Award Winner on 2007-02-05
How To Automatically Mount Sshfs and Other Network Filesystems That Don't Work in [FONT="Lucida Console"]/etc/fstab[/FONT].

Developed on: Edgy, x86
EDIT: THIS SOLUTION IS OBSOLETE! If you are running Feisty Fawn, YOU DO NOT NEED THIS! The version of Fuse in Feisty now supports fstab entries correctly. I am writing a howto for Feisty, and I will link to it when it is finished. Also, if you're somewhat adventurous but not adventurous to upgrade to Feisty, you can try the Fuse packages provided [here]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab"), which should be recent enough to work correctly with normal fstab entries: 

The problem: In Edgy, sshfs mounts don't seem to work in fstab, apparently because the mount.fuse program is missing, or something. In any case, it doean't work. Furthermore, even if it did, there is nothing to automatically mount these filesystems when the network is brought up and unmount them when the network is brought down. This last point was especially important to me because I have a laptop, so my network is constantly on an off, and any program trying to access a "dead" sshfs mount will hang, forcing you to kill it. The system I have devised below solves all of this. Additionally, it should be easy to modify this script to support fstab mounts when it becomes possible to use them.

Requirements: For this to work, you must be able to log into the remote system via ssh without having to type your password. For instructions on this, go [here]("http://doc.gwos.org/index.php/SecureSSH#Avoid_Using_Passwords"). Other than that, you must have sshfs installed and working. If you're not on edgy, then this howto will probably still work if your system has these directories:
[FONT="Lucida Console"]/etc/network/if-down.d
/etc/network/if-up.d[/FONT]

The Howto:
The procedure for setting this up involves adding three files to your system: one script for mounting, one for unmounting, and a configuration file to tell the scripts what to (un)mount. You do not have to modify any existing files, and you can undo any changes by simply deleting the new files.

First, the configuration file. As the name implies, the syntax is almost identical to the normal [FONT="Lucida Console"]/etc/fstab[/FONT]. Here is an example:

[FONT="Lucida Console"]/etc/fuse-fstab[/FONT]

```
# /etc/fuse-fstab: A workaround until full fstab fuse support arrives
# Syntax:
#device		mountpoint		fstype		options		user
# fstype is the program used to mount
# use "none" for no options. Don't leave it blank!!
luke@galaxy.farfaraway.com:       /home/luke/remotehome  sshfs       none   luke
vader@dstar2.empire.gov:/root/		/home/vader/deathstar     sshfs		reconnect  vader
```


The syntax:
device: This is the place you ssh into, followed by a colon, followed by the name of the directory you want access to.
mountpoint: This is where you want the remote directory to be mounted.
fstype: This is the *program* that will do the mounting (in our case, sshfs).
options: any options you wish to pass to the mounting program. (IMPORTANT: don't leave this blank! Leaving a field blank will cause an error (nothing bad will happen, the directory simply won't mount). If you have no options to pass, just put the word "none", as in the example above.
user: The owner of the mount.

Now, the mounting script:

[FONT="Lucida Console"]/etc/network/if-up.d/mountfuse[/FONT]

```
#!/bin/sh

do_start() {
    [ -f /etc/fuse-fstab ] || return
    
    exec 9<&0 </etc/fuse-fstab

    # comment this for testing
    exec 1>/dev/null # squelch echoes for non-interactive

	while read DEV MTPT FSTYPE OPTS USER REST; do
        LINE="$DEV $MTPT $FSTYPE $OPTS $USER $REST"

    	# skip comments and blank lines
	    case "$DEV" in
	        ""|\#*)
                continue
                ;;
	    esac

        # make sure all fields got set and no extra fields
        [ -z "$USER" ] && { echo "Not enough tokens: $LINE"; continue; }
        [ -n "$REST" ] && { echo "Too many tokens: $LINE"; continue; }

        
        # check if already mounted
	    grep $MTPT /etc/mtab 2>1 1>/dev/null && { echo "Already mounted: $MTPT"; continue; }

        # check if dir exists
	    [ -d $MTPT ] || { echo "Mount point does not exist or is not a directory: $MTPT"; continue; }
        
        # filter none and defaults from opts, and add fsname
        case "$OPTS" in
            "none")
                OPTS="fsname=$FSTYPE#$DEV"
                ;;
            *)
                OPTS="$OPTS,fsname=$FSTYPE#$DEV"
                ;;
        esac
        sudo -u $USER $FSTYPE -o $OPTS $DEV $MTPT && \
            echo "Succesfully mounted $DEV on $MTPT."
    done
}

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

# make sure the file exists
[ -f /etc/fuse-fstab ] || exit 0

# Lock around this otherwise insanity may occur
mkdir /var/run/network/mountfuse 2>/dev/null || exit 0

do_start

rmdir /var/run/network/mountfuse 2>/dev/null || exit 0
```


Lastly, the unmounting script:

[FONT="Lucida Console"]/etc/network/if-down.d/umountfuse[/FONT]

```
#!/bin/bash

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

# make sure the file exists
[ -f /etc/fuse-fstab ] || exit 0

exec 9<&0 </etc/fuse-fstab

# comment this for testing
exec 1>/dev/null # squelch output for non-interactive

while read DEV MTPT FSTYPE OPTS USER REST; do
        LINE="$DEV $MTPT $FSTYPE $OPTS $USER $REST"

    	# skip comments and blank lines
	    case "$DEV" in
	        ""|\#*)
                continue
                ;;
	    esac

        # make sure all fields got set and no extra fields
        [ -z "$USER" ] && { echo "Not enough tokens: $LINE"; continue; }
        [ -n "$REST" ] && { echo "Too many tokens: $LINE"; continue; }

        
        # umount if mounted
	    if grep $MTPT /etc/mtab 2>1 1>/dev/null ; then 
            umount -l $MTPT && \
            echo "Succesfully unmounted $MTPT."
        fi
done
```

Now make sure both scripts are executable:
```
sudo chmod +x /etc/network/if-up.d/mountfuse /etc/network/if-down.d/umountfuse
```

And you should be all set up. To try it out, restart your network. I believe the default command for this is:
```
sudo /etc/init.d/networking restart
```
You can also do it through the menu in System -> Administration -> Networking
If you use Network Manager, just right click on it and toggle "Enable Networking" off and on.
Then, to see the list of what's mounted, run the command:
```
mount
```

Your shares should show up. To make sure they also unmount correctly, stop the network:
```
sudo /etc/init.d/networking stop
```
and then run "mount" again to see if your shares disappeared from the list.

And that's it. 

Note: Nothing in this system is specific to sshfs. Other fuse filesystems, such as gnomevfs-mount, or even non-fuse filesystems, should work fine (just use "mount" for the fstype), but I haven't tested anything other than sshfs.

Credit: The structure of my "mountfuse" script is based on that of the already existing "/etc/network/if-up.d/mountnfs".

EDIT: Removed personal info from script, and small fix to comments in scripts. (No change in functionality.)

---

### Post by senor_jt on 2007-02-23
@Darwin...

I appreciate you taking the time to post this HOWTO.  Since discovering FUSE and SSHFS last year, I've played with various methods of automounting(and unmounting) my sshfs shares.  I've tried the debuntu.org repository for FUSE which should get you the latest and greatest version, supposedly with fstab support but have never been able to get it to work correctly.  I've been pondering the approach you took for a while but that would have required me to bone up on my shell skills.

So I was thrilled to come across your post!  And a bit surprised there hasn't been more activity on the thread... who doesn't have cheap, SSH accessible hosting these days?! :)  And SSHFS is an awesome gateway into that land of growing network file space.  Much better than webDAV.  

Alright, I'm through trying to rouse a bit more interest in the thread!  Long story short -- I created the three files on one of my systems, of course using my account information in the appropriate places, and it's just not working for me.  Specifically, mountfuse is not working.  Now here comes my uninformed/barely informed guesses -- assuming this works for you, might it be because we're using different FUSE/SSHFS versions?  Again, I've modified my apt repository and added debuntu.org in order to get the latest and greatest updates.  Perhaps there has been some change in versions that doesn't like your calling code?

I *can* still mount sshfs shares using sshfs [my_remote_username]@[my_remote_host]:[remotedir] [local_mountdir].  And calling your umountfuse with sudo ./umountfuse DOES successfully unmount the sshfs directory.  So the syntax of my /etc/fuse-fstab file seems to be correct(or so I infer).

Running sudo ./mountfuse with the exec 1>... line commented out gives me:
Password:
Password:
Password:
fsname=sshfs#[my_remote_username]@[my_remote_host]'s password:
fsname=sshfs#[my_remote_username]@[my_remote_host]'s password:
fsname=sshfs#[my_remote_username]@[my_remote_host]'s password:
remote host has disconnected

which I have taken to mean that my system really doesn't like the line,
sudo -u $USER $FSTYPE -o $OPTS $DEV $MTPT in the script.  But I'm still a freshman when it comes to shell scripting and my interpretations of what's going on and why are totally suspect.  Regarding the password queries above -- neither entering my local username password or the remote system password seem to make any difference.  It just cycles through the three attempts and exits as indicated.  Also, if you're wondering, I have successfully configured SSH with keys and do not have to enter the password when I use the sshfs command as I described far above.

Which of course leads me to the temptation of trying to modify your script -- strip out the sudo thang and just replace it with the sshfs command I use.  I understand there are almost certainly problems with that though due to user permissions?  Eh, I'll sit down and be quiet now.  

Do you -- does anyone -- have any suggestions on how to proceed?  My apologies in advance for my poor formatting.  Regardless, thanks again for sharing your approach.

--
jt

---

### Post by dare2dreamer on 2007-03-10
To get the mountfuse script working, change this line:

sudo -u $USER $FSTYPE -o $OPTS $DEV $MTPT && \

To read like this:

sudo -u $USER $FSTYPE $DEV $MTPT -o $OPTS && \

---

### Post by Nikron on 2007-03-11
Does anyone know a way to get this working with passwords?  
Don't really want to create keys because ...  it would be inconvenient

---

### Post by Darwin Award Winner on 2007-05-01
If you've upgraded to Feisty Fawn, disregard this thread. The reason for this solution was that mounting fuse filesystems using /etc/fstab was not possible with the version of Fuse in Edgy Eft. I have no idea if it is still impossible in Edgy, but in Feisty, this can now be done. I'll write a howto for using the normal fstab to mount sshfs shares soon, and I'll post a link to it here when it's done.

As for the problem of getting a bunch of password prompts, this solution will only work if you can do passwordless logins using a public/private key pair. There are all sorts of howto's and wizards for setting this up. 

Another solution might be a program called sshpass. It's in the repositories, and it's designed to provide a password non-interactively to ssh. Sshfs has an option so specify a program other than ssh, so there's definitely a possibility there, but you'll have to experiment on your own.

---

