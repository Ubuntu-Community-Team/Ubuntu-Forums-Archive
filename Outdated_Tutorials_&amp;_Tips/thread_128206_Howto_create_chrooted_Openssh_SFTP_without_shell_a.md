---
title: "Howto create chrooted Openssh SFTP without shell access through rssh."
date: 2006-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by jchau on 2006-02-10
[SIZE="5"][COLOR="Navy"][CENTER]This functionality now comes standard in OpenSSH using the ChrootDirectory and the ForceCommand keyword in sshd_config!  Hurray!  :KS[/CENTER][/COLOR][/SIZE]

The Match keyword also allows you to specify which users are affected.  This means that rssh and the setup outlined in this howto are no longer necessary.  From the sshd_config man page:
```
     ChrootDirectory
             Specifies a path to chroot(2) to after authentication.  This
             path, and all its components, must be root-owned directories that
             are not writable by any other user or group.

             The path may contain the following tokens that are expanded at
             runtime once the connecting user has been authenticated: %% is
             replaced by a literal '%', %h is replaced by the home directory
             of the user being authenticated, and %u is replaced by the user&#8208;
             name of that user.

             The ChrootDirectory must contain the necessary files and directo&#8208;
             ries to support the users' session.  For an interactive session
             this requires at least a shell, typically sh(1), and basic /dev
             nodes such as null(4), zero(4), stdin(4), stdout(4), stderr(4),
             arandom(4) and tty(4) devices.  For file transfer sessions using
             “sftp”, no additional configuration of the environment is neces&#8208;
             sary if the in-process sftp server is used (see Subsystem for
             details).

             The default is not to chroot(2).


``````
     ForceCommand
             Forces the execution of the command specified by ForceCommand,
             ignoring any command supplied by the client and ~/.ssh/rc if
             present.  The command is invoked by using the user's login shell
             with the -c option.  This applies to shell, command, or subsystem
             execution.  It is most useful inside a Match block.  The command
             originally supplied by the client is available in the
             SSH_ORIGINAL_COMMAND environment variable.  Specifying a command
             of “internal-sftp” will force the use of an in-process sftp
             server that requires no support files when used with
             ChrootDirectory.

``````
     Match   Introduces a conditional block.  If all of the criteria on the
             Match line are satisfied, the keywords on the following lines
             override those set in the global section of the config file,
             until either another Match line or the end of the file.

             The arguments to Match are one or more criteria-pattern pairs.
             The available criteria are User, Group, Host, and Address.  The
             match patterns may consist of single entries or comma-separated
             lists and may use the wildcard and negation operators described
             in the PATTERNS section of ssh_config(5).

             The patterns in an Address criteria may additionally contain
             addresses to match in CIDR address/masklen format, e.g.
             “192.0.2.0/24” or “3ffe:ffff::/32”.  Note that the mask length
             provided must be consistent with the address - it is an error to
             specify a mask length that is too long for the address or one
             with bits set in this host portion of the address.  For example,
             “192.0.2.0/33” and “192.0.2.0/8” respectively.

             Only a subset of keywords may be used on the lines following a
             Match keyword.  Available keywords are AllowAgentForwarding,
             AllowTcpForwarding, Banner, ChrootDirectory, ForceCommand,
             GatewayPorts, GSSAPIAuthentication, HostbasedAuthentication,
             KbdInteractiveAuthentication, KerberosAuthentication,
             MaxAuthTries, MaxSessions, PasswordAuthentication,
             PermitEmptyPasswords, PermitOpen, PermitRootLogin,
             RhostsRSAAuthentication, RSAAuthentication, X11DisplayOffset,
             X11Forwarding and X11UseLocalHost.


```

You should probably use the functionality built into OpenSSH instead, but just in case you don't want to do so, below is the tutorial as it was, which was last edited on February 5th, 2008 at 08:10 PM.  



Howto create chrooted Openssh SFTP without shell access through rssh.

I noticed many people wanted to set up a secure way (non cleartext and authentication required) to transfer files but wanted to limit their users from accessing a shell or browsing the entire file system.  For the past week, I have been searching for a way to do this myself.  

However, most of the solutions posted to these requests didn't suit me: chrootssh ([http://chrootssh.sourceforge.net/)](http://chrootssh.sourceforge.net/)), which I found difficult to set up since it involved compiling from source instead of installing from a package; set up another ftp server (like vsftpd), since I already had sshd running, I didn't want to manage another server and I was having difficulty getting this to work securely; setting the user's shell to the sftp-server, which still allowed to user to get out of their directories (but limited the user to sftp).  

I also tried rssh unsuccessfully once before finding a HOWTO from the gentoo-wiki website [<http://www.gentoo-wiki.com/index.php?title=HOWTO_SFTP_Server_(chrooted%2C_without_shell)&redirect=no>]("http://www.gentoo-wiki.com/index.php?title=HOWTO_SFTP_Server_(chrooted%2C_without_shell)&redirect=no"). (Many thanks to them).  I adapted their HOWTO slightly to work for Ubuntu.

It took me a week to finally set it up and get it working since I started trying.  I hope this HOWTO will help anyone else who wants to do this, but since I am writing this HOWTO after I set it up, I may accidentally forget a step.  In addition, my system may differ from your's (FYI, Ubuntu Breezy with i686 kernel; but even if you have the same, your configs may differ).  I make no guarantees that this will work on your system.  I am just writing this in hopes that it will help.  Feel free to post any suggestions/comments/questions/corrections.  NOTE: I only tested my setup for SFTP. 

First, you need the "openssh-server" package. (I assume you already have that installed, updated, and configured.  If not, it is pretty easy to do so & there are other tutorials available.  You can get it through Synaptic Package Manager.)

Then get the "rssh" package through Synaptic or through apt-get.

Once that is ready, you can configure rssh by editing the file "/etc/rssh.conf".  (You probably want to make a backup copy of that file by typing the command:
```
sudo cp /etc/rssh.conf /etc/rssh.orig.conf
```

The command I used to edit /etc/rssh.conf was :
```
sudo nano /etc/rssh.conf
```
Note: you need the nano text editor to do this. replace "nano" with "gedit" or another text editor if you want.  

The file should already be mostly filled out.  Just uncomment (by removing the '#') the lines "#allowsftp" to allow sftp and if you want, uncomment the line "#allowscp".  I left "#allowscp" commented since I only wanted sftp.  

There should be a line in "/etc/rssh.conf" that currently reads:
```
#chrootpath = "/usr/local/chroot dir"
```
change it to:
```
chrootpath = "/home/chroot"
```
(uncomment the line and change the path to "/home/chroot". The path is personal preference, but I decided "/home/chroot".) Doing this tells rssh to chroot jail everyone using rssh to the directory "/home/chroot".

At this point, your rssh.conf file should have the following uncommented lines:
```
logfacility = LOG_USER
allowsftp
umask = 022
chrootpath = "/home/chroot"

```

Now to make sure OpenSSH does not weaken rssh (gunzip and read "/usr/share/doc/rssh/SECURITY" for more information), make sure you have the latest package for openssh-server and run the following command:
```
cat /etc/ssh/sshd_config | grep "PermitUserEnvironment"
```

If you see the line beginning with "PermitUserEnvironment", use your text editor to either remove the line from "/etc/ssh/sshd_config" or to change the line to 
```
PermitUserEnvironment=no
```

Now to build the chrooted directory.  There should be a zipped script at "/usr/share/doc/rssh/examples/mkchroot.sh.gz".  Unzip the file, make a copy and edit the copy. You can do so using the following series of commands
```
sudo gunzip /usr/share/doc/rssh/examples/mkchroot.sh.gz
sudo cp /usr/share/doc/rssh/examples/mkchroot.sh ~/mkchroot.sh
sudo nano ~/mkchroot
```

If you scroll through the file, you will find the lines:
```
scp_path="/usr/bin/scp"
sftp_server_path="/usr/lib/sftp-server"
rssh_path="/usr/bin/rssh"
chroot_helper_path="/usr/lib/rssh/rssh_chroot_helper"
```

Make sure these paths match the ones given when you type the following command:
```
rssh -v
```

If they do not match, change your script so the paths match. 

If your setup is like mine, your sftp server will actually be located in "/usr/lib/openssh/sftp-server" instead of "/usr/lib/sftp-server", which is where rssh thinks the sftp-server is.  If this is your case, change
```
sftp_server_path="/usr/lib/sftp-server"
```
to
```
sftp_server_path="/usr/lib/openssh/sftp-server"
```

Save the script and exit the editor.

Then make the script executable with the following command:
```
sudo chmod u+x ~/mkchroot.sh
```


Now remember how you made
```
chrootpath = "/home/chroot"
```
in "/etc/rssh"? Well, now you actually make the chroot directory by running the following commands:
```
cd ~
sudo ./mkchroot.sh /home/chroot
```

While running that command, don't worry if you get the error saying that it cannot copy "linux-gate.so.1". It isn't a real file.  However, you will probably need to copy the file "ld-linux.so.2" if it appears when you type the command:
```
ldd /usr/bin/scp | grep "ld-linux.so.2"
```
but is not in the path "/home/chroot/lib/ld-linux.so.2".  You can copy the file with the following commands:
```
cd /home/chroot
sudo cp /lib/ld-linux.so.2 lib/
```

Just to play it safe, make sure you have "libnss_compat.so.2" in the directory "/home/chroot/lib".  If not, put it there with the following command:
```
sudo cp /lib/libnss_compat.so.2 /home/chroot/lib/
```

Now make rssh a valid shell by running the command:
```
add-shell /usr/bin/rssh
```

Now create a new user (I called mine "sft" for secure file transfer).  Make the shell for the new user "/usr/bin/rssh".  Make sure the home directory path is inside the chroot jail.  For me, I made the home directory "/home/chroot/home/sft".  If you don't know how to add a user, there is a GUI under System -> Administration -> Users and Groups.  


Now to apply the finishing touches and tie up loose ends:

For logging to work properly, you need to tell sysklogd to listen to "/home/chroot/dev/log".  You can do this by editing "/etc/init.d/sysklogd".  
*WARNING: You can seriously mess up your system logging if you mess up here.  BE CAREFUL! *
(you can replace nano with your text editor of choice).  Run the following to edit "/etc/init.d/sysklogd":
```
sudo nano /etc/init.d/sysklogd
```

You should find a line that starts with: 
```
SYSLOGD=
```
Simply add the following in the appropriate space on the line:
```
-a /home/chroot/dev/log
```
If your config is like mine, the original line will read:
```
SYSLOGD="-u syslog"
```
The new line will read:
```
SYSLOGD="-a /home/chroot/dev/log -u syslog"
```

You will need to tell sysklogd to restart to get the new config; use the following command:
```
sudo /etc/init.d/sysklogd restart
```

From what I read online, some programs may need /etc/passwd in order to run properly (I think scp).  To play it safe, place a copy of /etc/passwd in the chroot directory using the following command:
```
sudo cp /etc/passwd /home/chroot/etc/
```

For security reasons, you will probably want to remove all irrelevant lines from the passwd file in "/home/chroot/etc/".  So for my passwd file, since the name of the account that will use this chrooted directory, I only have the line: 
```
sft:x:1001:1001:Secure File Transfer Account,,,:/home/sft:/usr/bin/rssh
```

*WARNING: Please edit only the chroot copy of the passwd file, not the real one in /etc/passwd. *
You can use nano or another text editor to remove the other lines.  (I also changed the home directory in the chroot passwd file from "/home/chroot/home/sft" to "/home/sft".  I'm not sure if this is necessary, but I did this because I felt this will be better.)


In order for the chrooting process to work, "/usr/lib/rssh/rssh_chroot_helper" has to be setuid root.  (Note: this path is relative to real root, not chroot root.) To setuid root, run the command:
```
sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper
```


Now remember how rssh thinks that the sftp subsystem is located at "/usr/lib/sftp-server" but it is actually located in "/usr/lib/openssh/sftp-server"? If not, you can run the command:
```
rssh -v
```
to figure it out.  (Note: if this is not the case on your system, since our configs may differ, you should not follow this step and you should not follow one of the previous steps where you changed sftp_server_path="/usr/lib/sftp-server" to sftp_server_path="/usr/lib/openssh/sftp-server".)

If however, your sftp-server is located in "/usr/lib/openssh/" and rssh thinks that it is located in "/usr/lib/" and your sshd (ssh server) thinks that the sftp subsystem is located at "/usr/lib/openssh/", make the following changes.  (Note: you can check where sshd thinks the sftp subsystem is by the following command:
```
cat /etc/ssh/sshd_config | grep "Subsystem sftp "
```

First, create a link to "/usr/lib/openssh/sftp-server" at "/usr/lib/".  (Note: I already found a symbolic link to sftp-server in my "/usr/lib", so I kept it as a symbolic link.  However, a hard link seems more reasonable to me. I'll let you decide which one you want. If you don't know the difference between a symbolic link and a hard link, feel free to look it up; if you know how to explain the difference properly, please post an explanation.)

To create the symbolic link, use the command:
```
sudo ln -s /usr/lib/openssh/sftp-server /usr/lib/
```

To create the hard link, use the command:
```
sudo ln /usr/lib/openssh/sftp-server /usr/lib/
```

Now that the sftp-server exists in "/usr/lib", you can change the config file for your sshd.  Use your text editor to edit "/etc/ssh/sshd_config".  For me, the command was:
```
sudo nano /etc/ssh/sshd_config
```

Then find the line:
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
and replace it with:
```
Subsystem sftp /usr/lib/sftp-server
```

Save and exit the text editor when done.  In order for the new config to take effect, you need to tell sshd to reload the config using the following command:
```
sudo /etc/init.d/ssh reload
```

Now you have to fix your chroot directory setup (you need to be able to run "/usr/lib/sftp-server" even when chrooted).  To do this, create a hard link between for "/home/chroot/usr/lib/openssh/sftp-server" at "/home/chroot/usr/lib/" using the following command:
```
sudo ln /home/chroot/usr/lib/openssh/sftp-server /home/chroot/usr/lib/
```

Finally, there may be some files in the rsshed account's home directory like ".bashrc". If these are not needed, you can just delete them using the command "rm".

At this point, your setup should be done (unless you or I missed a step).  

Fire up your favorite SFTP client and test the new setup. Hopefully it will work.  Now try to ssh in using the rsshed account. A message should appear, and then rssh should exit, closing the connection.  

If you get a "connection closed" error and you have followed all the steps, adding null to your chrooted dev directory may help.  You can do this with the command
```
mknod -m 666 /home/chroot/dev/null c 1 3
```
where /home/chroot is the chroot directory.

Side note: If the user with the chrooted rsshed account manages to get to the server & get to the graphical login, they can login like a normal user (without chroot restrictions & without protection provided by rssh since the rssh shell is not the login shell).

**[COLOR="Red"]I have discovered that this setup will still allow people to use the port forwarding feature of SSH if it is enabled on the server.  See the blue section below for the fix.[/COLOR]**
[COLOR="Blue"]Update on AllowTcpForwarding:
You can use "Match" in your sshd_config to allow/disallow certain groups/users the ability to forward TCP connections.  Thanks to oojah for [this information]("http://ubuntuforums.org/showthread.php?p=2456617#post2456617").  (He placed the rssh users into a group called "chroot" in this example.)  [/COLOR]

---

### Post by jchau on 2006-02-22
I figured out how to avoid the GDM login loophole in security.  Disable GDM.  You can do this by going to System->Administration->Services. The uncheck "Graphical Login Manager (GDM)".  A warning message will appear.  Just continue. **WARNING: Continuing will stop your X session without further warning.**  

Now here is something funny.  Since X stopped, your settings did not save yet.  To actually make the change, you have to repeat.  

To get X back up:
```
startx
```
Then proceed back to System->Administration->Services.  You would notice that "Graphical Login Manager (GDM)" is still checked.  Uncheck it again & continue.  Click OK.  There GDM will not load anymore (until you check that box again).  

Now the user will have to log in through the text virtual terminal before X starts.  This lets rssh for the rsshed user run first, preventing those who aren't allowed to do anything but sftp from getting a normal login.  

For a normal user to get X, just run ```
startx
``` after logging in.  
For improved security, run ```
exec startx
```.  This prevents someone from simply pressing [Ctrl]+[Alt]+[F1] followed by [Ctrl]+[c] to get to your command prompt.  By putting exec in front of startx, this makes your account log out when your X session ends.  (To lock your X session, just go to System->Lock Screen.)  

Now your setup should work securely.  

However, if you run a laptop, you may notice a bug when you close your lid: your screen may not automatically turn back on after you open the lid again.  The reason is that the default lid.sh in "/etc/acpi/lid.sh" relies too much on X.  For more info, see [http://www.ubuntuforums.org/showthread.php?t=134319](http://www.ubuntuforums.org/showthread.php?t=134319).  

To fix this problem, replace the contents of lid.sh in "/etc/acpi/lid.sh" with:```
#!/bin/sh

# turns the screen off on lid close & on on lid open

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        sudo /usr/sbin/vbetool dpms off
else
        sudo /usr/sbin/vbetool dpms on
fi
```
(This requires the package "vbetool".  If you don't have this package, get it through apt-get or Synaptic.)

This code should shut off the screen when the lid is closed and turn the screen back on when the lid opens.  Note: it will not automatically lock your X session & it will not automatically lock your other virtual terminals.  To lock your X session, just go to System->Lock Screen.  

To lock your other virtual terminals, look into the package "vlock".  To use vlock, go to the virtual terminal you want to lock and type ```
vlock
``` or to lock all the terminals, type ```
vlock -a
```.

Now you can test this setup and hopefully celebrate \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ !

Any feedback is welcome. 
I'd like to turn this into a Wiki page, but I don't have the time to do the formatting checking & markup yet.

---

### Post by forkmantis on 2006-04-10
Excellent tutorial.  I got nearly everything squared away in one sitting.  

I ran into trouble when I attempted to symlink a shared directory into the chrooted home, but a little googling showed me that mount --bind is what I needed to solve the problem.  Hope this saves some frustration for anyone else who tries to do the same thing.  You can read more about it here:

[http://www.proftpd.org/localsite/Userguide/linked/chroot-symlinks.html](http://www.proftpd.org/localsite/Userguide/linked/chroot-symlinks.html)

---

### Post by jchau on 2006-04-11
Thanks. So that means I didn't miss a step! Great!

---

### Post by juicybananahead on 2006-04-14
Hi jchau,

I've been following your howto but I can't seem to get this working. ](*,) 

Somehow I know it's something simple but I'd appreciate any advice on how to set this up!

Obviously I don't want to put all of my sshd_config on the net but here are the outputs from a few commands:

cat /home/chroot/etc/passwd
```
sft:x:1004:1008:Secure File Transfer,,,:/home/sft:/usr/bin/rssh
```

cat /etc/rssh.conf
```
# This is the default rssh config file

# set the log facility.  "LOG_USER" and "user" are equivalent.
logfacility = LOG_USER

# Leave these all commented out to make the default action for rssh to lock
# users out completely...

#allowscp
allowsftp
#allowcvs
#allowrdist
#allowrsync

# set the default umask
umask = 022

# If you want to chroot users, use this to set the directory where the root of
# the chroot jail will be located.
#
# if you DO NOT want to chroot users, LEAVE THIS COMMENTED OUT.
# You can quote anywhere, but quotes not required unless path contains a
# space... as in this example.

chrootpath = "/home/chroot"

##########################################
# EXAMPLES of configuring per-user options

#user=rudy:077:00010:  # the path can simply be left out to not chroot
#user=rudy:077:00010   # the ending colon is optional

#spaces in the path must be quoted...
#user=rudy:011:00001:"/usr/local/chroot dir"  # scp with chroot
#user=rudy:011:00010:"/usr/local/chroot dir"  # sftp with chroot
#user=rudy:011:00011:"/usr/local/chroot dir"  # both with chroot
#user=rudy:011:00100:  # cvs, with no chroot
#user=rudy:011:01000:  # rdist, with no chroot
#user=rudy:011:10000:  # rsync, with no chroot
#user="rudy:011:00001:/usr/local/chroot"  # whole user string can be quoted
#user=rudy:01"1:00001:/usr/local/chroot"  # or somewhere in the middle, freak!
#user=rudy:'011:00001:/usr/local/chroot'  # single quotes too

# Spaces before or after the '=' are fine, but spaces in chrootpath need
# quotes.
#user = "rudy:011:00001:/usr/local/chroot dir"
#user = "rudy:011:00001:/usr/local/chroot dir"  # neither do comments at line end

```

cat mkchroot.sh
```

#!/bin/sh

#####################################################################
#####################################################################
##
## mkchroot.sh - set up a chroot jail.
##
## This script is written to work for Red Hat 8/9 systems, but may work on
## other systems.  Or, it may not...  In fact, it may not work at all.  Use at
## your own risk.  :)
##

fail() {

        echo "`basename $0`: fatal error" >&2
        echo "$1" >&2
        exit $2
}

#####################################################################
#
# Initialize - handle command-line args, and set up variables and such.
#
# $1 is the directory to make the root of the chroot jail (required)
# $2, if given, is the user who should own the jail (optional)
# $3, if given,  is the permissions on the directory (optional)
#

if [ -z "$1" ]; then
        echo "`basename $0`: error parsing command line" >&2
        echo "  You must specify a directory to use as the chroot jail." >&2
        exit 1
fi

jail_dir="$1"

if [ -n "$2" ]; then
        owner="$2"
fi

if [ -n "$3" ]; then
        perms="$3"
fi


#####################################################################
#
# build the jail
#

# now make the directory

if [ ! -d "$jail_dir" ]; then
        echo "Creating root jail directory."
        mkdir -p "$jail_dir"

        if [ $? -ne 0 ]; then
                echo "  `basename $0`: error creating jail directory." >&2
                echo "Check permissions on parent directory." >&2
                exit 2
        fi
fi

if [ -n "$owner" -a `whoami` = "root" ]; then
        echo "Setting owner of jail."
        chown "$owner" "$jail_dir"
        if [ $? -ne 0 ]; then
                echo "  `basename $0`: error changing owner of jail directory." >&2
                exit 3
         fi
else
        echo -e "NOT changing owner of root jail. \c"
        if [ `whoami` != "root" ]; then
                echo "You are not root."
        else
                echo
        fi
fi

if [ -n "$owner" -a `whoami` = "root" ]; then
        echo "Setting permissions of jail."
        chmod "$perms" "$jail_dir"
        if [ $? -ne 0 ]; then
                echo "  `basename $0`: error changing perms of jail directory." >&2
                exit 3
         fi
else
        echo -e "NOT changing perms of root jail. \c"
        if [ `whoami` != "root" ]; then
                echo "You are not root."
        else
                echo
        fi
fi

[COLOR="Red"]# copy SSH files

scp_path="/usr/bin/scp"
sftp_server_path="/usr/lib/openssh/sftp-server"
rssh_path="/usr/bin/rssh"
chroot_helper_path="/usr/lib/rssh/rssh_chroot_helper"[/COLOR]

for jail_path in `dirname "$jail_dir$scp_path"` `dirname "$jail_dir$sftp_server_path"` `dirname "$jail_dir$chroot_helper_path"`; do

        echo "setting up $jail_path"

        if [ ! -d "$jail_path" ]; then
                mkdir -p "$jail_path" || \
                        fail "Error creating $jail_path. Exiting." 4
        fi

done

cp "$scp_path" "$jail_dir$scp_path" || \
        fail "Error copying $scp_path. Exiting." 5
cp "$sftp_server_path" "$jail_dir$sftp_server_path" || \
        fail "Error copying $sftp_server_path. Exiting." 5
cp "$rssh_path" "$jail_dir$rssh_path" || \
        fail "Error copying $rssh_path. Exiting." 5
cp "$chroot_helper_path" "$jail_dir$chroot_helper_path" || \
        fail "Error copying $chroot_helper_path. Exiting." 5


#####################################################################
#
# identify and copy libraries needed in the jail
#

for prog in $scp_path $sftp_server_path $rssh_path $chroot_helper_path; do
        echo "Copying libraries for $prog."
        libs=`ldd $prog | tr -s ' ' | cut -d' ' -f3`
        for lib in $libs; do
                mkdir -p "$jail_dir$(dirname $lib)"
                echo -e "\t$lib"
                cp "$lib" "$jail_dir$lib"
        done
done

echo "copying name service resolution libraries..."
tar -cf - /lib/libnss_files* | tar -C "$jail_dir" -xvf - |sed 's/^/\t/'

#####################################################################
#
# copy config files for the dynamic linker, nsswitch.conf, and the passwd file
#

echo "Setting up /etc in the chroot jail"
mkdir -p "$jail_dir/etc"
cp /etc/nsswitch.conf "$jail_dir/etc/"
cp /etc/passwd "$jail_dir/etc/"
cp /etc/ld.* "$jail_dir/etc/"

echo -e "Chroot jail configuration completed."
echo -e "\nNOTE: if you are not using the passwd file for authentication,"
echo -e "you may need to copy some of the /lib/libnss_* files into the jail.\n"


#####################################################################
#
# set up /dev/log
#

mkdir -p "$jail_dir/dev"

echo -e "NOTE: you must MANUALLY edit your syslog rc script to start syslogd"
echo -e "with appropriate options to log to $jail_dir/dev/log.  In most cases,"
echo -e "you will need to start syslog as:\n"
echo -e "   /sbin/syslogd -a $jail_dir/dev/log\n"

echo -e "NOTE: we make no guarantee that ANY of this will work for you... \c"
echo -e "if it\ndoesn't, you're on your own.  Sorry!\n"

```

rssh -v
```
rssh 2.2.3
Copyright 2002-4 Derek D. Martin <rssh-discuss at lists dot sourceforge dot net>

    rssh config file = /etc/rssh.conf
  chroot helper path = /usr/lib/rssh/rssh_chroot_helper
     scp binary path = /usr/bin/scp
  sftp server binary = /usr/lib/sftp-server
     cvs binary path = /usr/bin/cvs
   rdist binary path = /usr/bin/rdist
   rsync binary path = /usr/bin/rsync

```

cat /etc/ssh/sshd_config | grep "Subsystem sftp "
```
Subsystem sftp /usr/lib/sftp-server
```

ls /usr/lib/sft* -l
```
lrwxrwxrwx  1 root root 28 2006-04-14 20:56 /usr/lib/sftp-server -> /usr/lib/openssh/sftp-server
```

ls /usr/lib/openssh/sft* -l
```
-rwxr-xr-x  1 root root 27184 2006-02-20 14:45 /usr/lib/openssh/sftp-server
```

 ls /home/chroot/usr/lib/openssh/* -l
```
-rwxr-xr-x  1 root root 27184 2006-04-14 20:44 /home/chroot/usr/lib/openssh/sftp-server
```

// Dave

---

### Post by juicybananahead on 2006-04-14
By the way - the problem seems to be that sftp-server doesn't run when I try to sftp in.

When I try "sftp sft@localhost" the following happens:

```
Connecting to localhost...
sft@localhost's password:
```

I enter the password and press enter...

```
Connection closed
```

Bah!

Thanks,
// Dave

---

### Post by jchau on 2006-04-14
did you setuid rssh_chroot_helper (the real one not the chroot dir one)?

If not, setuid it with
```
sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper
```

That might be causing the problem.  If

---

### Post by jchau on 2006-04-14
sorry for the slow response. I checked over your stuff and I can't find anything blatantly wrong.  Try the setuid thing and if that doesn't work, I'll try to get back to you Monday. (I'm packing for a trip home right now).

---

### Post by jchau on 2006-04-14
I tried unsetting root setuid on ```
/usr/lib/rssh/rssh_chroot_helper
```. It gives the same problem that you describe. so just run:
```
sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper
``` and you should be OK!:KS

---

### Post by juicybananahead on 2006-04-15
Hi Jimmy,

Slow response? Not at all! Cheers for getting back to me. Unfortunately I tried out your tip but it didn't work.

ls /usr/lib/rssh/rssh* -l
```
-rwsr-xr-x  1 root root 6680 2005-04-14 17:21 /usr/lib/rssh/rssh_chroot_helper
```

Don't know what's going on... Listen, enjoy your trip anyway. I'm off on one myself this afternoon so I'll be back after the weekend.

Take it easy,
// Dave

---

### Post by jchau on 2006-04-15
When you can, post rssh related log entries.  They should be in syslog.

Also try setting sftp into verbose mode with the -v option; eg.:
```
sftp -v -v sft@localhost
```

Meanwhile, I'll run over my howto to see if there are any pitfalls you might have hit.

(Sorry, I'm replying before Monday. Hope you don't mind)

---

### Post by jchau on 2006-04-15
Possible sources of the problem:
Does "/home/chroot/lib/ld-linux.so.2" exist? If not, ```
cd /home/chroot
sudo cp /lib/ld-linux.so.2 lib/
```
Just to play it safe, make sure you have "libnss_compact.so.2" in the directory "/home/chroot/lib". If not, put it there with the following command:```
sudo cp /lib/libnss_compact.so.2 /home/chroot/lib/
```
Did you add the lines to "/etc/init.d/sysklogd" (if so, there should be messages from rssh in syslog; post them.

Also make sure you did this step:
> Now you have to fix your chroot directory setup (you need to be able to run "/usr/lib/sftp-server" even when chrooted). To do this, create a hard link between for "/home/chroot/usr/lib/openssh/sftp-server" at "/home/chroot/[COLOR="Red"]usr/[/COLOR]lib/" using the following command:
```
sudo ln /home/chroot/usr/lib/openssh/sftp-server /home/chroot/[COLOR="Red"]usr/[/COLOR]lib/
```

Final note: make sure you remembered to tell sysklogd and sshd to reload after you changed the configs.

If all else fails, see if you can sftp with a normal (not rsshed) account (maybe it is the sftp-server)

If you don't have any private files in the /home/chroot, post the results for:
```
ls -lR /home/chroot/
``` so I can see if you are missing any necessary files in your chrooted directory.

Hope this helps (if it does, please tell me which one helped).

[COLOR="Red"]---
Note: the parts in red are added (not originally there).  Thanks to juicybananahead for discovering the error. For more information, see following two posts.  [/COLOR]

---

### Post by juicybananahead on 2006-04-16
Hi Jimmy,

Got it working! For your own peace of mind :D, here's the information you were looking for:

First, the verbose output of an sftp attempt.
```
user@ubuntubox:~$ sftp -v -v sft@localhost
Connecting to localhost...
OpenSSH_4.1p1 Debian-7ubuntu4.1, OpenSSL 0.9.7g 11 Apr 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.1p1 Debia n-7ubuntu4.1
debug1: match: OpenSSH_4.1p1 Debian-7ubuntu4.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4.1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-gro up14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-gro up14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 137/256
debug2: bits set: 483/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:8
debug2: bits set: 475/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/id_rsa ((nil))
debug2: key: /home/user/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
sft@localhost's password:
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug2: fd 4 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug2: channel 0: request env confirm 0
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 131072
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.3 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 1
Connection closed

```

Second, the syslog entries for the sftp attempt.
```
user@ubuntubox:~$ sudo cat /var/log/syslog | tail -8
Apr 16 23:34:16 localhost rssh[26642]: setting log facility to LOG_USER
Apr 16 23:34:16 localhost rssh[26642]: allowing sftp to all users
Apr 16 23:34:16 localhost rssh[26642]: setting umask to 022
Apr 16 23:34:16 localhost rssh[26642]: chrooting all users to /home/chroot
Apr 16 23:34:16 localhost rssh[26642]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper "/home/chroot" 2 "/home/sft" /usr/lib/sftp-server
Apr 16 23:34:17 localhost rssh_chroot_helper[26642]: new session for sft, UID=1004
Apr 16 23:34:17 localhost rssh_chroot_helper[26642]: could not cd to user's home dir: /home/sft
Apr 16 23:34:17 localhost rssh_chroot_helper[26642]: execv() failed, /usr/lib/sftp-server: No such file or directory

```

Alright, I first noticed that chrooted /home/sft (i.e. /home/chroot/home/sft) could not be cd'd to, so I created a directory like that but I didn't think that would have much of an effect... and right I was. Another failure to sftp. The syslog entries for this attempt:
```
user@ubuntubox:~$ sudo cat /var/log/syslog | tail -7
Apr 16 23:45:29 localhost rssh[26982]: setting log facility to LOG_USER
Apr 16 23:45:29 localhost rssh[26982]: allowing sftp to all users
Apr 16 23:45:29 localhost rssh[26982]: setting umask to 022
Apr 16 23:45:29 localhost rssh[26982]: chrooting all users to /home/chroot
Apr 16 23:45:29 localhost rssh[26982]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper "/home/chroot" 2 "/home/sft" /usr/lib/sftp-server
Apr 16 23:45:29 localhost rssh_chroot_helper[26982]: new session for sft, UID=1004
Apr 16 23:45:29 localhost rssh_chroot_helper[26982]: execv() failed, /usr/lib/sftp-server: No such file or directory
```

Okaaaay... now it's looking for /usr/lib/sftp-server (i.e. /home/chroot/usr/lib/sftp-server). Why is it looking for that? I thought it would be looking for /lib/sftp-server (i.e. /home/chroot/lib/sftp-server). Let's have a look at the entire contents of /home/chroot
```
user@ubuntubox:/home/chroot$ ls -lR
.:
total 20
drwxr-xr-x  2 root root 4096 2006-04-16 07:40 dev
drwxr-xr-x  2 root root 4096 2006-04-16 23:41 etc
drwxr-xr-x  3 root root 4096 2006-04-16 23:41 home
drwxr-xr-x  3 root root 4096 2006-04-16 23:45 lib
drwxr-xr-x  4 root root 4096 2006-04-14 20:44 usr

./dev:
total 0
srw-rw-rw-  1 root root 0 2006-04-16 07:40 log

./etc:
total 76
-rw-r--r--  1 root root 56431 2006-04-14 20:44 ld.so.cache
-rw-r--r--  1 root root    63 2006-04-14 20:44 ld.so.hwcappkgs
-rw-r--r--  1 root root   465 2006-04-14 20:44 nsswitch.conf
-rw-r--r--  1 root root    64 2006-04-16 23:41 passwd
-rw-r--r--  1 root root    76 2006-04-16 23:33 passwd~

./home:
total 4
drwxr-xr-x  2 root root 4096 2006-04-16 23:41 sft

./home/sft:
total 0

./lib:
total 260
-rwxr-xr-x  1 root root 88168 2006-04-14 20:47 ld-linux.so.2
-rw-r--r--  1 root root 26332 2006-04-14 20:49 libnss_compat.so.2
-rw-r--r--  1 root root 34268 2006-03-24 14:34 libnss_files-2.3.5.so
lrwxrwxrwx  1 root root    21 2006-04-14 20:44 libnss_files.so.2 -> libnss_files-2.3.5.so
-rw-r--r--  1 root root 68084 2006-04-14 20:44 libselinux.so.1
-rwxr-xr-x  2 root root 27184 2006-04-14 20:44 sftp-server
drwxr-xr-x  3 root root  4096 2006-04-14 20:44 tls

./lib/tls:
total 4
drwxr-xr-x  3 root root 4096 2006-04-14 20:44 i686

./lib/tls/i686:
total 4
drwxr-xr-x  2 root root 4096 2006-04-14 20:44 cmov

./lib/tls/i686/cmov:
total 1408
-rw-r--r--  1 root root   21864 2006-04-14 20:44 libcrypt.so.1
-rw-r--r--  1 root root 1229936 2006-04-14 20:44 libc.so.6
-rw-r--r--  1 root root    9580 2006-04-14 20:44 libdl.so.2
-rw-r--r--  1 root root   76760 2006-04-14 20:44 libnsl.so.1
-rw-r--r--  1 root root   67364 2006-04-14 20:44 libresolv.so.2
-rw-r--r--  1 root root    9656 2006-04-14 20:44 libutil.so.1

./usr:
total 8
drwxr-xr-x  2 root root 4096 2006-04-14 20:44 bin
drwxr-xr-x  5 root root 4096 2006-04-14 20:44 lib

./usr/bin:
total 56
-rwxr-xr-x  1 root root 18960 2006-04-14 20:44 rssh
-rwxr-xr-x  1 root root 34884 2006-04-14 20:44 scp

./usr/lib:
total 92
drwxr-xr-x  3 root root  4096 2006-04-14 20:44 i686
-rw-r--r--  1 root root 77208 2006-04-14 20:44 libz.so.1
drwxr-xr-x  2 root root  4096 2006-04-14 20:44 openssh
drwxr-xr-x  2 root root  4096 2006-04-14 20:44 rssh

./usr/lib/i686:
total 4
drwxr-xr-x  2 root root 4096 2006-04-14 20:44 cmov

./usr/lib/i686/cmov:
total 1004
-rw-r--r--  1 root root 1022224 2006-04-14 20:44 libcrypto.so.0.9.7

./usr/lib/openssh:
total 28
-rwxr-xr-x  2 root root 27184 2006-04-14 20:44 sftp-server

./usr/lib/rssh:
total 8
-rwsr-xr-x  1 root root 6680 2006-04-14 20:44 rssh_chroot_helper

```

Right, sftp-server is present in /home/chroot/usr/lib/openssh and /home/chroot/lib/. Now, let's make a link in /home/chroot/usr/lib...
```
user@ubuntubox:/home/chroot$ sudo ln /home/chroot/usr/lib/openssh/sftp-server /home/chroot/usr/lib/
```

And try to sftp in...
```
user@ubuntubox:~$ sftp sft@localhost
Connecting to localhost...
sft@localhost's password:
sftp> pwd
Remote working directory: /home/sft
sftp> ls
test.txt
sftp> get test.txt
Fetching /home/sft/test.txt to test.txt
/home/sft/test.txt                            100%    6     0.0KB/s   00:00
sftp> bye
user@ubuntubox:~$ cat ./test.txt
Successful sftp test!

```

Ta-daa! I am honestly not sure what went wrong during setup - was it because my /etc/sshd_config points at /usr/lib/sftp-server as the location of sftp-server?
```
user@ubuntubox:~$ cat /etc/ssh/sshd_config | grep sftp
Subsystem sftp /usr/lib/sftp-server
```

Anyway, I'm just glad to get it working. Thanks for your help, Jimmy!

// Dave

---

### Post by jchau on 2006-04-17
Oh, thanks. You found an error in my howto. I wrote> Now you have to fix your chroot directory setup (you need to be able to run "/usr/lib/sftp-server" even when chrooted). To do this, create a hard link between for "/home/chroot/usr/lib/openssh/sftp-server" at "/home/chroot/lib/" using the following command:```
sudo ln /home/chroot/usr/lib/openssh/sftp-server /home/chroot/lib/
```

It should be:
> Now you have to fix your chroot directory setup (you need to be able to run "/usr/lib/sftp-server" even when chrooted). To do this, create a hard link between for "/home/chroot/usr/lib/openssh/sftp-server" at "/home/chroot/[COLOR="Red"]usr/[/COLOR]lib/" using the following command:```
sudo ln /home/chroot/usr/lib/openssh/sftp-server /home/chroot/[COLOR="Red"]usr/[/COLOR]lib/
```

I'll be sure to correct this in the howto.  Thanks again. Sorry for the trouble.

---

### Post by jchau on 2006-04-17
Oh juicybananahead, you do not need sftp-server in /home/chroot/lib/. You can delete that one if you created it.

---

### Post by mega on 2006-04-27
i'm getting this error, any sugestions would be great

Apr 27 09:47:32 localhost rssh[25930]: command: /usr/lib/sftp-server
Apr 27 09:48:00 localhost rssh[25948]: setting log facility to LOG_USER
Apr 27 09:48:00 localhost rssh[25948]: setting umask to 022
Apr 27 09:48:00 localhost rssh[25948]: chrooting all users to /home/chroot
Apr 27 09:48:00 localhost rssh[25948]: user sft attempted to execute forbidden commands
Apr 27 09:48:00 localhost rssh[25948]: command: /usr/lib/sftp-server

---

### Post by mega on 2006-04-27
ahh found my problem, have to edit rssh.config and add sftp as an allowed command

---

### Post by chuckao on 2006-05-12
Hi,

I'm having the same Mega's problem, but my /etc/rssh.conf is correct.

```

May 13 00:30:47 localhost rssh[7527]: setting log facility to LOG_USER
May 13 00:30:47 localhost rssh[7527]: allowing scp to all users
May 13 00:30:47 localhost rssh[7527]: allowing sftp to all users
May 13 00:30:47 localhost rssh[7527]: setting umask to 022
May 13 00:30:47 localhost rssh[7527]: chrooting all users to /home/chroot
May 13 00:30:47 localhost rssh[7527]: user test attempted to execute forbidden commands
May 13 00:30:47 localhost rssh[7527]: command: /usr/lib/openssh/sftp-server

```

I can use the "scp" command, but I'm not having success with sftp. ](*,) 

Any idea?

[COLOR="Red"]Ps: Ok, my fault!! I found the problem, the sftp-server's path. This howto is perfectly correct but I don't know the real necessity of passwd file inside of jail. I don't have this file and jail works.[/COLOR]

---

### Post by OnlyJedi on 2006-05-13
I followed through with your tutorial, but I had a few differences...I'm running Dapper, so that's whats to be expected.  When I ran rssh -v, I had the following:
```
# rssh -v

rssh 2.3.0
Copyright 2002-5 Derek D. Martin <rssh-discuss at lists dot sourceforge dot net>
    rssh config file = /etc/rssh.conf
  chroot helper path = /usr/lib/rssh/rssh_chroot_helper
     scp binary path = /usr/bin/scp
  sftp server binary = /usr/lib/[COLOR="Red"]openssh/[/COLOR]sftp-server
     cvs binary path = /usr/bin/cvs
   rdist binary path = /usr/bin/rdist
   rsync binary path = /usr/bin/rsync

```
This means that rssh thinks the sftp-server command is in /usr/lib/openssh, correct?  So, I setup the mkchroot.sh script as follows
```
# nano ~/mkchroot.sh
...
scp_path="/usr/bin/scp"
sftp_server_path="/usr/lib/[COLOR="Red"]openssh/[/COLOR]sftp-server"
rssh_path="/usr/bin/rssh"
chroot_helper_path="/usr/lib/rssh/rssh_chroot_helper"
...

```
Now for the part about creating the sym/hard links and editing /etc/ssh/sshd_config, I shouldn't need to do that since rssh knows the proper directory for sftp-server, correct?  I didn't think so at first, so I skipped over that part and finished the tutorial, but when I try to log in I immediately get a connection closed after typing the correct password, and my logs show
```
# cat /var/log/syslog | tail -8
May 13 12:38:33 localhost rssh[22813]: setting umask to 022
May 13 12:38:33 localhost rssh[22813]: chrooting all users to /media/files/pub
May 13 12:38:33 localhost rssh[22813]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
May 13 12:38:33 localhost rssh_chroot_helper[22813]: new session for sft, UID=10000
May 13 12:38:33 localhost rssh_chroot_helper[22813]: user's home dir is /media/files/pub/home/sft
May 13 12:38:33 localhost rssh_chroot_helper[22813]: chrooted to /media/files/pub
May 13 12:38:33 localhost rssh_chroot_helper[22813]: changing working directory to /home/sft (inside jail)
May 13 12:38:33 localhost rssh_chroot_helper[22813]: execv() failed, /usr/lib/openssh/sftp-server: Permission denied

```
So, I went through the linking + editing process, and got the same error logging in, but a different error in the logs:
```
# cat /var/log/syslog | tail -8
May 13 12:59:31 localhost rssh[23480]: user sft attempted to execute forbidden commands
May 13 12:59:31 localhost rssh[23480]: command: /usr/lib/sftp-server
May 13 13:01:40 localhost rssh[23644]: setting log facility to LOG_USER
May 13 13:01:40 localhost rssh[23644]: allowing sftp to all users
May 13 13:01:40 localhost rssh[23644]: setting umask to 022
May 13 13:01:40 localhost rssh[23644]: chrooting all users to /media/files/pub
May 13 13:01:40 localhost rssh[23644]: user sft attempted to execute forbidden commands
May 13 13:01:40 localhost rssh[23644]: command: /usr/lib/sftp-server

```
I'm pretty sure that log contains two failed login attempts, not just one, as can be seen from the timestamps.  So it seemed I was right the first time, but that still leaves the permission error.  I checked, and rssh_chroot_helper is set chmod u+s, both the real file and the chrooted one.  Both the real and chrooted sftp-server files are executable by world, and their directories can be read/browsed by world.  So I'm stuck now; anybody have any ideas what the problem is?

Before I forget, my /etc/rssh/rssh.config
```
# cat /etc/rssh/rssh.config
# This is the default rssh config file

# set the log facility.  "LOG_USER" and "user" are equivalent.
logfacility = LOG_USER

# Leave these all commented out to make the default action for rssh to lock
# users out completely...

#allowscp
allowsftp
#allowcvs
#allowrdist
#allowrsync

# set the default umask
umask = 022

# If you want to chroot users, use this to set the directory where the root of
# the chroot jail will be located.
#
# if you DO NOT want to chroot users, LEAVE THIS COMMENTED OUT.
 chrootpath = "/media/files/pub"

# You can quote anywhere, but quotes not required unless the path contains a
# space... as in this example.
#chrootpath = "/usr/local/my chroot"

##########################################
# EXAMPLES of configuring per-user options

#user=rudy:077:00010:  # the path can simply be left out to not chroot
#user=rudy:077:00010   # the ending colon is optional

#user=rudy:011:00100:  # cvs, with no chroot
#user=rudy:011:01000:  # rdist, with no chroot
#user=rudy:011:10000:  # rsync, with no chroot
#user="rudy:011:00001:/usr/local/chroot"  # whole user string can be quoted
#user=rudy:01"1:00001:/usr/local/chroot"  # or somewhere in the middle, freak!
#user=rudy:'011:00001:/usr/local/chroot'  # single quotes too

# if your chroot_path contains spaces, it must be quoted...
# In the following examples, the chroot_path is "/usr/local/my chroot"
#user=rudy:011:00001:"/usr/local/my chroot"  # scp with chroot
#user=rudy:011:00010:"/usr/local/my chroot"  # sftp with chroot
#user=rudy:011:00011:"/usr/local/my chroot"  # both with chroot

# Spaces before or after the '=' are fine, but spaces in chrootpath need
# quotes.
#user = "rudy:011:00001:/usr/local/my chroot"
#user = "rudy:011:00001:/usr/local/my chroot"  # neither do comments at line end

```
And the relevant line from /etc/passwd (present in the chrooted directory)
```
# cat passwd
sft:x:10000:10000:New User,,,:/home/sft:/usr/bin/rssh

```

Let me know if you need more info.

EDIT:
OK, I wasn't thinking.  I had the filesystem the chrooted environment was in mounted noexec, so of course I was getting permission denied errors.  A simple remount solved my problem.

---

### Post by jchau on 2006-05-15
[QUOTE=chuckao][COLOR="Red"]Ps: Ok, my fault!! I found the problem, the sftp-server's path. This howto is perfectly correct but I don't know the real necessity of passwd file inside of jail. I don't have this file and jail works.[/COLOR][/QUOTE]

I added this because I adapted this from the gentoo one.  They mentioned it, so I figured that I'd add it too.  I think it is only needed for scp though.

---

### Post by jchau on 2006-05-15
Sorry for for the slow response, I'm usually faster, but my I didn't have my computer for a while.  If rssh knows the proper path for the sftp server, you shouldn't have to go through the extra trouble of creating the links to the right place.  I don't have a solution for you yet, but I'll take another look.

Edit:
whoops.  didn't read your edit, OnlyJedi.  Glad you got it to work.

---

### Post by jchau on 2006-05-15
[QUOTE=OnlyJedi]I checked, and rssh_chroot_helper is set chmod u+s, both the real file and the chrooted one.  Both the real and chrooted sftp-server files are executable by world, and their directories can be read/browsed by world.  [/QUOTE]
About this: you should probably unsetuid the rssh_chroot_helper in the chroot directory.  It doesn't need to be chrooted, and it is probably insecure.

---

### Post by jchau on 2006-06-14
For those who have problem with the rssh setup after upgrading to Dapper from Breezy, there is a new thread for Dapper describing how to fix problems arising from the install.  [http://ubuntuforums.org/showthread.php?t=195266](http://ubuntuforums.org/showthread.php?t=195266)

---

### Post by erat123 on 2006-08-29
I'm having a little trouble with this.  Instead of using /home as a directory, i'm storing the path in /var/www/home

Everything worked fine, and i created a user with this command:

useradd eric -s /usr/bin/rssh -d /var/www/home/eric

it created the user just fine, then i did a 'passwd eric' to set the password.  then i took the /etc/passwd file and placed it in /var/www/home/etc and removed all the lines except 'eric'.

no errors or anything, but when i try to log in, it just says access denied.  i'm using winscp to try to get a visual of this working.  i also tried PuTTY to get access, but it also says access denied.  please help!!!

thanks,
Eric

---

### Post by jchau on 2006-08-30
I do not recall seeing the error "access denied" and I cannot successfully recreate that error.  Please make sure you followed every step.  

A sshd setting may also be causing the problem (you did not allow password authentication).  This is the most likely cause of that error that I found.  See [http://www.ubuntuforums.org/showthread.php?t=7842](http://www.ubuntuforums.org/showthread.php?t=7842) for more information.

If that still doesn't help, please post the exact error message you get, note when the error appears, and also post the relevant log entries.  See [http://ubuntuforums.org/showpost.php?p=925617&postcount=11](http://ubuntuforums.org/showpost.php?p=925617&postcount=11) for more information.  

Also, the point of this setup is to prevent shell access so you should not be able to connect with PuTTY; you should be presented with the following followed by a disconnect:
> This account is restricted by rssh.
Allowed commands: sftp

If you believe this is in error, please contact your system administrator.


---

### Post by jax2000 on 2006-09-04
Hi,

Thanks for a great howto. I have a problem with user accounts. When I add a new user and then login from another computer everything seems to be ok. But user is still able to explore out of his home dir and download files like /etc/passwd/ and others :confused: Shouldn't the user be jailed in it's home dir ? not just /home/chroot/ or what ?

---

### Post by jchau on 2006-09-04
> **jax2000 said:**
> Hi,

Thanks for a great howto. I have a problem with user accounts. When I add a new user and then login from another computer everything seems to be ok. But user is still able to explore out of his home dir and download files like /etc/passwd/ and others :confused: Shouldn't the user be jailed in it's home dir ? not just /home/chroot/ or what ?

You're welcome!

If you followed the instructions, the user should still be able to see files like /etc/passwd.  However, these files should not be the files on the real root (remember copying these files to the chroot directory?).  These files should also have no information that can comprimise your system's security (remember removing all the unnecessary lines from the chroot copy of /etc/passwd? your system should also be using shadow, so no password hashes will be stored in /etc/passwd either).  

Since sftp and rssh depends on the presence of certain files, the files need to be copied to the chroot folder.  For clarification, the chroot jail prevents the jailed user from leaving the jail (in my case, /home/chroot/), not their home directory in the chroot jail (/home/chroot/home/sft/).  So for example, the user sft in my howto can access /home/chroot/etc/nsswitch.conf (which will appear to be /etc/nsswitch.conf to the sft), but sft will not be allowed to access the real /etc/nsswitch.conf.  

You might now be wondering why you would want to use a chroot jail.  One advantage is damage control; if your user somehow compromises your sftp server, they should not be able to mess with the real root, only the chroot jail.  Another is increased security: they will not be able to access files outside of the chroot jail even if your file permissions somehow allow it (though you should fix your file permissions anyway); eg. your home (outside the chroot jail) directory may be world readable, but you might have a confidential document stored in it or you might not want to let someone find out by looking through /usr/local/bin that you have some package installed.  There are probably a few other advantages too.  

If you don't feel that the chroot jail is worth the trouble, you can also forgo that altogether and just use rssh without the chroot jail (simply make the user's account by specifying rssh as a shell, don't specify a home directory, and comment the chrootpath from rssh.conf).  

As an easy way to check to see if your users can get out of the chroot jail, you can see if the user can access the file "/etc/ssh/ssh_config".  It is in the real root, but should not be in the chroot root.  If they can get to the file, stop your ssh server or disable the accounts and make sure that you followed all the steps.  You can also put a file in the real root and see if the chroot jailed users can access the file.

---

### Post by jax2000 on 2006-09-06
I understand that jailing users inside this "fake system" is a lot safer way to go. I did edit the /etc and other folder permissions so even if users can browse the folders they cannot see the files. Even if it does not really matter :)

---

### Post by jchau on 2006-09-12
[B][COLOR="Red"]I have discovered that this setup will still allow people to use the port forwarding feature of SSH if it is enabled on the server.  A temporary fix is to disallow TCPForwarding completely for everyone.  This can be done by adding the following line to /etc/ssh/sshd_config:```
AllowTcpForwarding no
```
Then reload the new config with the following command:```
sudo /etc/init.d/ssh reload
```[/COLOR][/B]

If anyone has any ideas about how to prevent only the rssh users from using TCP forwarding feature or to allow only certain users to have that ability, I'd be glad to see it!  The sshd_config(5) man page seems to suggest that the latter should be possible by saying the following:> Note that disabling TCP forwarding does not improve security unless users are also denied shell access, as they can always install their own forwarders.

I have modified the first post of this thread to include this information, but I'm hoping this new reply will cause everyone subscribed to this thread to receive this notice.

---

### Post by aprita on 2006-12-02
I've been trying to setup a rssh with chroot jail on ubuntu 6.10 pretty much out of the box and was able to get a nice configure working with openssh and mysecureshell. I'm now interested in rssh b/c it supports rsync as well and followed the excellent howto provided in this post. Sadly things didn't quite want to work out that well and since google wasn't able to help me I'm hoping I'll find some help here.

What happens: after following through the howto and log on to my host through sftp I get a simple Connection closed after inputting the password. The complete log that gets generated looks like this:

```
rssh[6291]: setting log facility to LOG_USER
rssh[6291]: allowing sftp to all users
rssh[6291]: allowing rsync to all users
rssh[6291]: setting umask to 022
rssh[6291]: chrooting all users to /home/office
rssh[6291]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```

when I try to log into the shh using an account for which rssh is setup I get the following output in the terminal:

```
This account is restricted by rssh.
Allowed commands: sftp rsync

If you believe this is in error, please contact your system administrator.

*** glibc detected *** -rssh: malloc(): memory corruption: 0x0804fc78 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e2b1cd]
/lib/tls/i686/cmov/libc.so.6(malloc+0x7f)[0xb7e2c83f]
-rssh[0x804a485]
-rssh[0x804aceb]
-rssh[0x804b33c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7dd98cc]
-rssh[0x8048aa1]
======= Memory map: ========
08048000-0804d000 r-xp 00000000 08:04 2900436    /usr/bin/rssh
0804d000-0804e000 rwxp 00004000 08:04 2900436    /usr/bin/rssh
0804e000-0806f000 rwxp 0804e000 00:00 0          [heap]
b7c00000-b7c21000 rwxp b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7d84000-b7d8e000 r-xp 00000000 08:04 1196099    /lib/libgcc_s.so.1
b7d8e000-b7d8f000 rwxp 00009000 08:04 1196099    /lib/libgcc_s.so.1
b7d8f000-b7d98000 r-xp 00000000 08:04 1229074    /lib/tls/i686/cmov/libnss_files-2.4.so
b7d98000-b7d9a000 rwxp 00008000 08:04 1229074    /lib/tls/i686/cmov/libnss_files-2.4.so
b7d9a000-b7da2000 r-xp 00000000 08:04 1229076    /lib/tls/i686/cmov/libnss_nis-2.4.so
b7da2000-b7da4000 rwxp 00007000 08:04 1229076    /lib/tls/i686/cmov/libnss_nis-2.4.so
b7da4000-b7db6000 r-xp 00000000 08:04 1229071    /lib/tls/i686/cmov/libnsl-2.4.so
b7db6000-b7db8000 rwxp 00011000 08:04 1229071    /lib/tls/i686/cmov/libnsl-2.4.so
b7db8000-b7dba000 rwxp b7db8000 00:00 0 
b7dba000-b7dc1000 r-xp 00000000 08:04 1229072    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7dc1000-b7dc3000 rwxp 00006000 08:04 1229072    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7dc3000-b7dc4000 rwxp b7dc3000 00:00 0 
b7dc4000-b7ef1000 r-xp 00000000 08:04 1229065    /lib/tls/i686/cmov/libc-2.4.so
b7ef1000-b7ef3000 r-xp 0012c000 08:04 1229065    /lib/tls/i686/cmov/libc-2.4.so
b7ef3000-b7ef5000 rwxp 0012e000 08:04 1229065    /lib/tls/i686/cmov/libc-2.4.so
b7ef5000-b7ef8000 rwxp b7ef5000 00:00 0 
b7f0a000-b7f0c000 rwxp b7f0a000 00:00 0 
b7f0c000-b7f25000 r-xp 00000000 08:04 1196245    /lib/ld-2.4.so
b7f25000-b7f27000 rwxp 00018000 08:04 1196245    /lib/ld-2.4.so
bfbc0000-bfbd6000 rw-p bfbc0000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Connection to **** closed.
```

I don't know if this is relevant, but I setup my ssh server on a nonstandard port and used the home directory of the user as the chroot jail directory (since only one user will be using the rssh shell). Also when I remove the option to use the chroot in the rssh.conf file, everything works fine. (I am able to log in through sftp and terminal doesn't provide a crash report when trying to log in through ssh (it simply states connection closed and that's it)).

Any help would be greatly appreciated. If you need more info, please let me know. Thanks.

---

### Post by jchau on 2006-12-02
> **aprita said:**
> 
*** glibc detected *** -rssh: malloc(): memory corruption: 0x0804fc78 ***


:-k hmmm, I've seen the "Connection closed" before & it can be caused by a variety of problems: wrong file permissions, missing libraries in the chroot directory, using a disallowed protocol, or just about anything that might cause rssh to quit.  

However, I never seen the memory corruption error from.  The logical next step would be to run memcheck to see if it's the physical memory's fault.  However, I'm not sure if the error should persist if it was bad memory.  

The next step should be to check to see if all the libraries needed are available, in the correct location, and up-to date in the chroot directory.  To double check, you can use ldd on the binaries.  For example, 
```
jimmy@Jimmy-Laptop:~$ ldd `which scp`
        linux-gate.so.1 =>  (0xffffe000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7f03000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7dc9000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7dc4000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7db0000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7d9a000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7d6c000)
        libselinux.so.1 => /lib/libselinux.so.1 (0xb7d58000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7d3c000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7cbf000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7c9a000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7c95000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7c92000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b5e000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b5a000)
        libsepol.so.1 => /lib/libsepol.so.1 (0xb7b1c000)
        /lib/ld-linux.so.2 (0xb7f2b000)

```

Notice that "linux-gate.so.1" does not have a corresponding file location.  You can safely ignore this library (it should be readily available from memory).  However, also notice that "/lib/ld-linux.so.2" doesn't follow the format that the others do.  Because the format in which this library is presented is different, the mkchroot.sh script will not copy this one; you will need to copy this one manually.  

When checking the libraries, pay special attention to the ones mentioned in the error.  To play it safe, you can just copy all of them over again.  

If that doesn't work, we can do some more pondering later.  Strange thing about the memory error though is that it appears after rssh tells you that your account is restricted; it normally exits immediately after that.  This makes me think that your problem is also caused by something else.

---

### Post by aprita on 2006-12-03
Thanks a lot for your quick reply. As you suggested I did a memcheck but nothing showed up. I saw through googling that there are a few memchecks out there. Anyone particular you had in mind? I simply used the memtest+86 which is provided in the GRUB boot manager. 

I also went through the libraries and hand copied all of them as you suggested. Same result ... 

Here my output for the ldd check:

```
user@goofy:/home/office/lib$ ldd `which sftp`
        linux-gate.so.1 =>  (0xffffe000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7ef8000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7dbe000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7db9000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7da5000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7d8f000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7d61000)
        libselinux.so.1 => /lib/libselinux.so.1 (0xb7d4d000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7d31000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7cb4000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7c8f000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7c8a000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7c87000)
        libedit.so.2 => /usr/lib/libedit.so.2 (0xb7c6b000)
        libncurses.so.5 => /lib/libncurses.so.5 (0xb7c2b000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7af6000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7af2000)
        libsepol.so.1 => /lib/libsepol.so.1 (0xb7ab5000)
        /lib/ld-linux.so.2 (0xb7f1f000)
user@goofy:/home/office/lib$ ldd `which scp`
        linux-gate.so.1 =>  (0xffffe000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7f8a000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7e50000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7e4b000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7e37000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7e21000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7df3000)
        libselinux.so.1 => /lib/libselinux.so.1 (0xb7ddf000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7dc3000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7d46000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7d21000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7d1c000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7d19000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7be5000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7be1000)
        libsepol.so.1 => /lib/libsepol.so.1 (0xb7ba3000)
        /lib/ld-linux.so.2 (0xb7fb1000)

```

I then even copied the entire /lib/ folder to the chroot /lib/ folder as was suggested in a different post. Same result ... After that I commented out the chroot option in the rssh.conf file and everything worked fine again without the chroot jail. 

I don't know if this is relevant, but when I compare the output from the log file with other users on the web they have some statements after 

```
rssh[6291]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```

or a slightly different argument for the rss_chroot_helper. Could these problems come from the rss_chroot_helper? 

Is there any other kind of log files or such that would be able to provide some more insight into this problem? (I'm still kinda new to linux and don't really know it inside and out yet) 
Once again, thanks a bunch for your help.

---

### Post by jchau on 2006-12-04
> **aprita said:**
> Thanks a lot for your quick reply. As you suggested I did a memcheck but nothing showed up. I saw through googling that there are a few memchecks out there. Anyone particular you had in mind? I simply used the memtest+86 which is provided in the GRUB boot manager. 

I then even copied the entire /lib/ folder to the chroot /lib/ folder as was suggested in a different post. Same result ... After that I commented out the chroot option in the rssh.conf file and everything worked fine again without the chroot jail. 

I don't know if this is relevant, but when I compare the output from the log file with other users on the web they have some statements after 

```
rssh[6291]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```

or a slightly different argument for the rss_chroot_helper. Could these problems come from the rss_chroot_helper? 

Is there any other kind of log files or such that would be able to provide some more insight into this problem? (I'm still kinda new to linux and don't really know it inside and out yet) 
Once again, thanks a bunch for your help.

memtest is fine; that was the one I was thinking of anyway.  

about rssh_chroot_helper.  make sure the one in the real root is suid root (needs to run as root).  also make sure that there is a usr/lib/openssh/sftp-server in your chroot directory.  some people have noexec set on their home partition; if /home is a different partition, make sure this isn't the case.  make sure the user you are using has access to and own their home folder; their home folder should be in the chroot directory.  

you can add a few -v options to get some more verbosity when using sftp to try to pin-point the problem.  

as for the command logged, I don't see anything particular about it; what did you notice?


BTW, this week is the last week of classes for me and my professors decided to play catch-up with the syllabus by assigning loads of work, so I probably won't respond again until next week.

---

### Post by aprita on 2006-12-05
so, out of some kind of magic I am now not getting the memory error anymore when attempting to log in using ssh. It now nicely rejects me and closes the connection. Honestly cannot say what I did that would have caused it. Didn't restart the machine or anything. Just hoping it'll still like this now ...

The problem with not being able to log in using sftp still pertains and probably due to chroot. I checked and rssh_chroot_helper does indeed have suid root. Further the home directory is on the same partition and the user has ownership and access to it. Also there is a sftp-server in the chroot directory with execution permission from owner (root) through world. I added two -v's to my sftp login attempts and this is was I got (I wasn't able to extract anything useful, but maybe you can):

```
siddha@goofy:~$ sftp -v -v -oPort=2255 office@localhost
Connecting to localhost...
OpenSSH_4.3p2 Debian-5ubuntu1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 2255.
debug1: Connection established.
debug1: identity file /home/siddha/.ssh/id_rsa type -1
debug1: identity file /home/siddha/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 132/256
debug2: bits set: 528/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/siddha/.ssh/known_hosts:1
debug2: bits set: 519/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/siddha/.ssh/id_rsa ((nil))
debug2: key: /home/siddha/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/siddha/.ssh/id_rsa
debug1: Trying private key: /home/siddha/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 1
Password:
debug2: input_userauth_info_req
debug2: input_userauth_info_req: num_prompts 0
debug1: Authentication succeeded (keyboard-interactive).
debug2: fd 4 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 131072
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 1
Connection closed
```

I don't know if this matters but I set my sftp server to a non-standard port (2255). 

Further, as for the command logging. My log files end with outputs from the rssh executable, but do not receive any outputs from rssh_chroot_helper like juicybananahead or OnlyJedi got in their previous posts in this thread. My log file ends with the line:

```

rssh[6291]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```

no comments such as (tooken from OnlyJedi):
```
May 13 12:38:33 localhost rssh_chroot_helper[22813]: new session for sft, UID=10000
May 13 12:38:33 localhost rssh_chroot_helper[22813]: user's home dir is /media/files/pub/home/sft
May 13 12:38:33 localhost rssh_chroot_helper[22813]: chrooted to /media/files/pub
May 13 12:38:33 localhost rssh_chroot_helper[22813]: changing working directory to /home/sft (inside jail)
```

Does this mean that possibly rssh_chroot_helper is never called? or is it possibly not logging it?

Hope your profs didn't load you too badly. I myself am also enjoying the fun week before finals rush on projects and studying as well. Good luck with all your stuff!

---

### Post by aprita on 2006-12-05
never mind ... after rebooting my machine and trying to logging in through shh I get the same crash again. :(

---

### Post by edylie on 2006-12-16
I am running ubuntu 6.10 and for those getting the connection closed message, make sure you have null in your /home/chroot/dev directory

if it does not exist, excute the following command

sudo mknod -m 666 /home/chroot/dev/null c 1 3

cheers,
Edy

---

### Post by aprita on 2006-12-16
wow, now that's what I called problem solved (for me at least) :-D. Thanks so much for your help edy and jchau! How did you figure that out edy? 

The null dev fixed my sftp login problems, as for my memory crash.... What I have noticed is that when I leave my machine on for a while (say over night after a fresh reboot) the crash can't be reproduced the next morning and it appears to work the way it should. Have no idea how to find out why and what is causing it but figure it's only marginally related to this program but more so to the underlying OS. If anyone has any ideas on what could be causing this they would be greatly appreciated. 

Thanks a again for all your help guys,
aprita

---

### Post by jchau on 2006-12-17
Thanks edylie.  I forgot about that; the Gentoo guide mentioned it too.  I added it to the original Howto post.

---

### Post by aprita on 2007-01-02
In case anyone would be interested in using rssh and rsync (wrapped using ssh) along with a chroot jail and you successfully followed through the howto kindly provided by jchau but ran into a problem like the following when using rsync :

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)

try copying:
/usr/bin/rsync into the jail (e.g. /home/jail/usr/bin/rsync) and 
/lib/libpopt.so.0 into the jail as well (e.g. /home/jail/lib/libpopt.so.0)

Helped me and hope it'll help you as well.
Cheers,
aprita

---

### Post by neo4242002 on 2007-02-06
Hi genius… First of all thanks you very much for this wonderful Howto. Something I been searching for long time.

I am kind of a newbee to this type of work. But I enjoy them learning. So I need some help from experts. I am using Ubuntu 6.10 Server (Edgy Eft) and I have followed all setups without missing anything.  But I am still unable to work SFTP in my server. 

CAN SOMEONE HELP ME PLEASE :( 

I had couple of problems during the installation and everything passed her for you guys reference.


```
rssh -v

rssh 2.3.2
Copyright 2002-5 Derek D. Martin <rssh-discuss at lists dot sourceforge dot net>

    rssh config file = /etc/rssh.conf
  chroot helper path = /usr/lib/rssh/rssh_chroot_helper
     scp binary path = /usr/bin/scp
  sftp server binary = /usr/lib/openssh/sftp-server
     cvs binary path = /usr/bin/cvs
   rdist binary path = /usr/bin/rdist
   rsync binary path = /usr/bin/rsync
```


[PHP]nano ~/mkchroot.sh

scp_path="/usr/bin/scp"
sftp_server_path="/usr/lib/openssh/sftp-server"
rssh_path="/usr/bin/rssh"
chroot_helper_path="/usr/lib/rssh/rssh_chroot_helper"
[/PHP]


```
:~# ./mkchroot.sh /home/chroot
-e NOT changing owner of root jail.
-e NOT changing perms of root jail.
setting up /home/chroot/usr/bin
setting up /home/chroot/usr/lib/openssh
setting up /home/chroot/usr/lib/rssh
Copying libraries for /usr/bin/scp.
-e      (0xffffe000)
cp: cannot stat `(0xffffe000)': No such file or directory
-e      /lib/tls/i686/cmov/libresolv.so.2
-e      /usr/lib/i686/cmov/libcrypto.so.0.9.8
-e      /lib/tls/i686/cmov/libutil.so.1
-e      /usr/lib/libz.so.1
-e      /lib/tls/i686/cmov/libnsl.so.1
-e      /lib/tls/i686/cmov/libcrypt.so.1
-e      /lib/libselinux.so.1
-e      /usr/lib/libgssapi_krb5.so.2
-e      /usr/lib/libkrb5.so.3
-e      /usr/lib/libk5crypto.so.3
-e      /usr/lib/libkrb5support.so.0
-e      /lib/libcom_err.so.2
-e      /lib/tls/i686/cmov/libc.so.6
-e      /lib/tls/i686/cmov/libdl.so.2
-e      /lib/libsepol.so.1
Copying libraries for /usr/lib/openssh/sftp-server.
-e      (0xffffe000)
cp: cannot stat `(0xffffe000)': No such file or directory
-e      /lib/tls/i686/cmov/libresolv.so.2
-e      /usr/lib/i686/cmov/libcrypto.so.0.9.8
-e      /lib/tls/i686/cmov/libutil.so.1
-e      /usr/lib/libz.so.1
-e      /lib/tls/i686/cmov/libnsl.so.1
-e      /lib/tls/i686/cmov/libcrypt.so.1
-e      /lib/libselinux.so.1
-e      /usr/lib/libgssapi_krb5.so.2
-e      /usr/lib/libkrb5.so.3
-e      /usr/lib/libk5crypto.so.3
-e      /usr/lib/libkrb5support.so.0
-e      /lib/libcom_err.so.2
-e      /lib/tls/i686/cmov/libc.so.6
-e      /lib/tls/i686/cmov/libdl.so.2
-e      /lib/libsepol.so.1
Copying libraries for /usr/bin/rssh.
-e      (0xffffe000)
cp: cannot stat `(0xffffe000)': No such file or directory
-e      /lib/tls/i686/cmov/libc.so.6
Copying libraries for /usr/lib/rssh/rssh_chroot_helper.
-e      (0xffffe000)
cp: cannot stat `(0xffffe000)': No such file or directory
-e      /lib/tls/i686/cmov/libc.so.6
copying name service resolution libraries...
tar: Removing leading `/' from member names
        lib/libnss_compat-2.4.so
        lib/libnss_compat.so.2
        lib/libnss_files-2.4.so
        lib/libnss_files.so.2
Setting up /etc in the chroot jail
cp: omitting directory `/etc/ld.so.conf.d'
-e Chroot jail configuration completed.
-e
NOTE: if you are not using the passwd file for authentication,
-e you may need to copy some of the /lib/libnss_* files into the jail.

-e NOTE: you must MANUALLY edit your syslog rc script to start syslogd
-e with appropriate options to log to /home/chroot/dev/log.  In most cases,
-e you will need to start syslog as:

-e    /sbin/syslogd -a /home/chroot/dev/log

-e NOTE: we make no guarantee that ANY of this will work for you... -e if it
doesn't, you're on your own.  Sorry!
```


```
root@buzz:/home# ls -l
total 16
drwxr-xr-x 7 root     root     4096 2007-02-06 18:27 chroot
drwxr-xr-x 2 root     root     4096 2007-02-06 17:46 chroot.
drwxr-xr-x 2 ftp      nogroup  4096 2007-02-06 15:37 ftp

```


```
/home# ldd /usr/bin/scp | grep "ld-linux.so.2"
        /lib/ld-linux.so.2 (0xb7fde000)


```


```
/home/chroot# ls -al /home/chroot/lib
total 476
drwxr-xr-x 3 root root   4096 2007-02-06 19:36 .
drwxr-xr-x 7 root root   4096 2007-02-06 18:27 ..
-rwxr-xr-x 1 root root 105112 2007-02-06 19:39 ld-linux.so.2
-rw-r--r-- 1 root root   5560 2007-02-06 19:36 libcom_err.so.2
-rw-r--r-- 1 root root  26332 2007-01-24 22:19 libnss_compat-2.4.so
lrwxrwxrwx 1 root root     20 2007-02-06 19:36 libnss_compat.so.2 -> libnss_compat-2.4.so
-rw-r--r-- 1 root root  34276 2007-01-24 22:19 libnss_files-2.4.so
lrwxrwxrwx 1 root root     19 2007-02-06 19:36 libnss_files.so.2 -> libnss_files-2.4.so
-rw-r--r-- 1 root root  75228 2007-02-06 19:36 libselinux.so.1
-rw-r--r-- 1 root root 203552 2007-02-06 19:36 libsepol.so.1
drwxr-xr-x 3 root root   4096 2007-02-06 17:46 tls
```


```
/home/chroot# cp /lib/libnss_compact.so.2 /home/chroot/lib/
cp: cannot stat `/lib/libnss_compact.so.2': No such file or directory
```

```

useradd -d /home/chroot/home/sft -s /usr/bin/rssh sft

```

```

/home/chroot# cat /etc/ssh/sshd_config | grep "Subsystem sftp "
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp /usr/lib/sftp-server

```


```
/home/chroot# ln -s /usr/lib/openssh/sftp-server /usr/lib/
ln: creating symbolic link `/usr/lib/sftp-server' to `/usr/lib/openssh/sftp-server': File exists

```


```
# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp /usr/lib/sftp-server

```

```
:/home/chroot# ln /home/chroot/usr/lib/openssh/sftp-server /home/chroot/usr/lib/
ln: creating hard link `/home/chroot/usr/lib/sftp-server' to `/home/chroot/usr/lib/openssh/sftp-server': File exists
```


I just worry about that "File Exists", other than that everything made exactly on this Howto. I have also noticed my file making following error when i try to FTP. Also my Putty get close automatically just after type my password. Any ideas guys?:confused: :confused: 

```
Status:	Connecting to 192.168.101.8:22 ...
Status:	Connected with 192.168.101.8:22, initializing SFTP connection...
Command:	CONNECT sft@192.168.101.8:22
Response:	Fatal: unable to initialise SFTP: could not connect
Error:	Unable to connect!
Status:	Waiting to retry... (5 retries left)
```

---

### Post by aschaef on 2007-02-09
So after a few hours I've gotten this working with a user I have created.  I only have one issue.  When I am logged in with WinSCP I am able to hit the "go up one level" icon and access all files above the user's home dir.  Is there any way to lock them just in that directory so they can't view any higher level dirs?

Thanks.

---

### Post by jchau on 2007-02-10
> **aschaef said:**
> So after a few hours I've gotten this working with a user I have created.  I only have one issue.  When I am logged in with WinSCP I am able to hit the "go up one level" icon and access all files above the user's home dir.  Is there any way to lock them just in that directory so they can't view any higher level dirs?

Thanks.

The rssh user should not be able to "acess _all_ files."  They should be stuck inside the chroot directory (eg. /home/chroot in the guide).  While that may look like the real root directory (/) with a bunch of files from the real root directory, the files your rssh user should see are only a copy of the real files that rssh needs to run; the files are there because rssh, or the sftp server will need them (even when they are in the chroot directory).  

I haven't figured out how to prevent users from leaving their home directory on a sftp session, but this greatly limits what they can access and what they can do.

---

### Post by ashembers on 2007-02-21
I just wanted to say thanks to jchau. This is really nice. Works with FileZilla as well as WinSCP too.

---

### Post by jchau on 2007-02-21
> **ashembers said:**
> I just wanted to say thanks to jchau. This is really nice. Works with FileZilla as well as WinSCP too.

You're welcome!

---

### Post by alex_marshall on 2007-02-21
Hey everyone,

I've got a somewhat new problem: I'm unable to get rssh going with SFTP.  I've read all of the above posts in the thread, and tried all of the solutions, and still nothing works.  I've ensured that all of my paths match up, and still nothing works.

rssh -v :
<code>
rssh 2.3.2
Copyright 2002-5 Derek D. Martin <rssh-discuss at lists dot sourceforge dot net>

    rssh config file = /etc/rssh.conf
  chroot helper path = /usr/libexec/rssh_chroot_helper
     scp binary path = /usr/bin/scp
  sftp server binary = /usr/libexec/openssh/sftp-server
     cvs binary path = /usr/bin/cvs
   rdist binary path = /usr/bin/rdist
   rsync binary path = /usr/bin/rsync
</code>

grep -v "#" /etc/rssh.conf
<code>
logfacility = LOG_USER 
allowscp
allowsftp
umask = 022
chrootpath = "/home/dropbox"
</code>

Relevant contents of mkchroot.sh :
<code>
scp_path="/usr/bin/scp"
sftp_server_path="/usr/libexec/openssh/sftp-server"
rssh_path="/usr/bin/rssh"
chroot_helper_path="/usr/libexec/rssh_chroot_helper"
</code>

ls -l /usr/libexec/rssh_chroot_helper :
<code>
-rwsr-xr-x    1 root     root        51557 Aug 13  2006 /usr/libexec/rssh_chroot_helper
</code>

...and still nothing works.  If I've forgotten to post something relevant, please let me know and I'll post it.  I have to get this working because I NEED a jailed directory with SFTP and scponly doesn't cut it.

SCP works fine, but when I try to use SFTP to copy :
ie : sftp [myusername]@localhost:~
Results in : Connection Closed.
I've already copied the Kerberos libs to $CHROOTJAIL/lib (which was the deciding factor in getting SCP working), but still SFTP doesn't work.  I'm absolutely desperate to get this working and I would appreciate any help. Please.

---

### Post by jchau on 2007-02-21
Is your ssh server configured to use /usr/libexec/openssh/sftp-server for the sftp server? check you sshd config file.  Also, can you post the relavent log entries (/var/log/messages)?  That might give a hint about where rssh is failing.

---

### Post by jchau on 2007-02-21
neo4242002,

Sorry, I missed your post.  There seems to be a number of problems:
o The "-e" is a parameter for echo.  It shouldn't be displayed in the output.  
o The error, "cp: cannot stat `/lib/libnss_compact.so.2': No such file or directory" means that cp couldn't find the file.  Make sure you spelled the filename correctly.  
o As for your linking, I am not sure what you are trying to do.  I don't think it is necessary for Edgy.

See if correcting these problems will fix it.  

BTW, you're **supposed to** get rejected while trying to log in to a rssh account using PuTTY; a normal ssh session would give the user shell access.  That's one of the reasons why you're going through all of this trouble.

---

### Post by ashembers on 2007-02-22
I don't know if anyone else had mentioned this, but I thought I might offer that it helps ease users minds when they cannot see the chrooted home directory & as such not see other users' home dirs. So I can offer these commands that also work well: 
> cd /home/chroot
sudo chmod 771 home

This should work if root is the owner, which it should be at this point. Through the Ubuntu UI I also like to make sure no access is given to Others for any users home dir, but that is up to you. </unsolicited advice>

Hope that helps!

---

### Post by shookone on 2007-02-27
For EDGY Users..

To relieve the "Exit Status: 0" Closed connection issue. Refer to the Dapper version of this tutorial mentioned in this thread.

Great job on this thread!

---

### Post by dhonn on 2007-04-08
I'm running FEISTY and ran into some errors. 

```
Apr  8 19:52:47 localhost rssh[20240]: user issac attempted to execute forbidden commands
Apr  8 19:52:47 localhost rssh[20240]: command: /usr/lib/sftp-server
```

I followed everything to a T but WinSCP was giving the error:
```
Cannot initialize SFTP protocol. Is the host running a SFTP server?
Connection has been unexpectedly closed. Server sent command exit status 0.

```

**But I got it to work..** here is what I changed to make it work:

I simply changed:
```
Subsystem sftp /usr/lib/sftp-server
```

To this:
```
Subsystem sftp /usr/lib/openssh/sftp-server
```

Don't forget to reload ssh..
```
sudo /etc/init.d/ssh reload
```

Perhaps this will helps others.  But maybe I got something wrong in my initial configuration.  If you know what I did wrong initially let me know.

---

### Post by oojah on 2007-04-15
> **jchau said:**
> 
If anyone has any ideas about how to prevent only the rssh users from using TCP forwarding feature or to allow only certain users to have that ability, I'd be glad to see it!

Easy! :)

openssh allows you to specify rules per user/group. So in my sshd_config I have:

```

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       ForceCommand cvs server
Match Group chroot
        AllowTcpForwarding no

```

Cheers,

Roger

---

### Post by Poka64 on 2007-04-15
I'm getting this error when I try to connect with Winscp:

Error skipping startup message. Your shell is probably incompatible with the application (BASH is recommended).

---

### Post by jetpeach on 2007-04-20
i was very excited when i first saw this thread, but then as i scrolled down the howto i got disappointed. i really appreciate the hard work you've put into writing this, but i'm totally disappoint there isn't an easier way. has anybody written a script that would just do all of it for us? or what about these "jailer  Builds and maintains chrooted environments" programs available? will they be easier?
i love ubuntu and like playing around on my computer plenty, but i don't want to have to go through all these steps. but perhaps there is no easier way, and perhaps i should try writing the script or my own program. i guess i just thought it would be easier than all this.

---

### Post by jchau on 2007-04-22
> **oojah said:**
> Easy! :)

openssh allows you to specify rules per user/group. So in my sshd_config I have:

```

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       ForceCommand cvs server
Match Group chroot
        AllowTcpForwarding no

```

Cheers,

Roger

Thanks.  I'll add this to the original post.  I hope u don't mind.

---

### Post by jchau on 2007-04-22
> **Poka64 said:**
> I'm getting this error when I try to connect with Winscp:

Error skipping startup message. Your shell is probably incompatible with the application (BASH is recommended).

I've never seen that before.  Have u tried another client?  Or do all clients give this error message.  what happens when u do
```
sftp rsshuser@localhost
```
from the server?  (Replace rsshuser with the user name).

---

### Post by jchau on 2007-04-22
> **jetpeach said:**
> i was very excited when i first saw this thread, but then as i scrolled down the howto i got disappointed. i really appreciate the hard work you've put into writing this, but i'm totally disappoint there isn't an easier way. has anybody written a script that would just do all of it for us? or what about these "jailer  Builds and maintains chrooted environments" programs available? will they be easier?
i love ubuntu and like playing around on my computer plenty, but i don't want to have to go through all these steps. but perhaps there is no easier way, and perhaps i should try writing the script or my own program. i guess i just thought it would be easier than all this.

Writing a script to do this is possible, but I haven't see any available to completely automate this process.  (BTW, most of this howto is modifying the mkchroot.sh script to fit your system.)  If you know how to write such a script, that'll be awesome.  There are also plenty of other options.  This was the one that I liked the best.  Feel free to suggest better alternatives.  

If you go through these steps manually though, you'll probably understand the setup better though.

---

### Post by aschaef on 2007-04-25
I have the SFTP server up and running with the great instructions in this post.  I was just trying to figure out how I can log: Time of Connection, User, File Transfered, and Logoff, or better yet if the logging is already happening, where the files are.  Thanks.

---

### Post by cypher35 on 2007-05-15
Upon logging in to the newly created account via ssh, I am prompted to change my password.

I plan on having this account used by multiple people, so I don't want them to have the ability to change the password.  Is there a way to prevent this behavior?


Also, I am having trouble getting sftp to work.  Here is my log file:
```
May 15 15:27:38 scud rssh[15221]: setting log facility to LOG_USER
May 15 15:27:38 scud rssh[15221]: allowing sftp to all users
May 15 15:27:38 scud rssh[15221]: setting umask to 022
May 15 15:27:38 scud rssh[15221]: chrooting all users to /home/chroot
May 15 15:27:38 scud rssh[15221]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```

I noticed that there are no "rssh_chroot_helper" lines following this.  Is this component not being loaded?


I am also missing two files referenced within the setup:
**/lib/ld-linux.so.2**
**/lib/libnss_compact.so.2**

For the first one, I assume that my equivalent is "**/lib/ld-linux-x86-64.so.2**" since I'm running amd64 feisty.  Would I need to copy this as **/home/chroot/lib/ld-linux.so.2**, or leave the name as it is and copy it to **/home/chroot/lib/ld-linux-x86-64.so.2**?

The second file doesn't seem to have an equivalent.  Could you possibly have meant "**/lib/libnss_compat.so.2**" ("compat" not "compact")?


Any help would be greatly appreciated.

---

### Post by reech on 2007-05-17
Hi - I'm using dapper (amd64) - and having big problems.

here is my setup (I have created my chroot dir in /usr/local as I'd like to keep the /home dir mounted with noexec): 

```

/usr/local/chroot:
total 20
drwxr-xr-x 2 root root 4096 2007-05-17 06:25 dev
drwxr-xr-x 2 root root 4096 2007-05-16 13:06 etc
drwxr-xr-x 3 root root 4096 2007-05-16 13:09 home
drwxr-xr-x 2 root root 4096 2007-05-16 13:07 lib
drwxr-xr-x 4 root root 4096 2007-05-16 13:06 usr

/usr/local/chroot/dev:
total 0
srw-rw-rw- 1 root root    0 2007-05-17 06:25 log
crw-rw-rw- 1 root root 1, 3 2007-05-16 13:11 null

/usr/local/chroot/etc:
total 40
-rw-r--r-- 1 root root 27266 2007-05-16 13:06 ld.so.cache
-rw-r--r-- 1 root root   195 2007-05-16 13:06 ld.so.conf
-rw-r--r-- 1 root root   470 2007-05-16 13:06 nsswitch.conf
-rw-r--r-- 1 root root  1303 2007-05-17 11:03 passwd

/usr/local/chroot/home:
total 4
drwxr-xr-x 2 cheers cheers 4096 2007-05-16 13:09 cheers

/usr/local/chroot/home/cheers:
total 0

/usr/local/chroot/lib:
total 1940
-rwxr-xr-x 1 root root   92868 2007-05-16 13:07 ld-linux.so.2
-rw-r--r-- 1 root root    8040 2007-05-16 13:06 libcom_err.so.2
-rw-r--r-- 1 root root   20376 2007-05-16 13:06 libcrypt.so.1
-rwxr-xr-x 1 root root 1267512 2007-05-16 13:06 libc.so.6
-rw-r--r-- 1 root root   10056 2007-05-16 13:06 libdl.so.2
-rw-r--r-- 1 root root   83424 2007-05-16 13:06 libnsl.so.1
-rw-r--r-- 1 root root   36112 2007-05-16 13:07 libnss_compat.so.2
-rw-r--r-- 1 root root   44056 2007-05-16 13:08 libnss_files-2.3.6.so
lrwxrwxrwx 1 root root      21 2007-05-16 13:06 libnss_files.so.2 -> libnss_files-2.3.6.so
-rw-r--r-- 1 root root   75288 2007-05-16 13:06 libresolv.so.2
-rw-r--r-- 1 root root   82624 2007-05-16 13:06 libselinux.so.1
-rw-r--r-- 1 root root  212376 2007-05-16 13:06 libsepol.so.1
-rw-r--r-- 1 root root    9864 2007-05-16 13:06 libutil.so.1

/usr/local/chroot/usr:
total 8
drwxr-xr-x 2 root root 4096 2007-05-16 13:06 bin
drwxr-xr-x 4 root root 4096 2007-05-17 10:55 lib

/usr/local/chroot/usr/bin:
total 64
-rwxr-xr-x 1 root root 24096 2007-05-16 13:06 rssh
-rwxr-xr-x 1 root root 40752 2007-05-16 13:06 scp

/usr/local/chroot/usr/lib:
total 2400
-rw-r--r-- 1 root root 1495336 2007-05-16 13:06 libcrypto.so.0.9.8
-rw-r--r-- 1 root root  120064 2007-05-16 13:06 libgssapi_krb5.so.2
-rw-r--r-- 1 root root  150552 2007-05-16 13:06 libk5crypto.so.3
-rw-r--r-- 1 root root  548448 2007-05-16 13:06 libkrb5.so.3
-rw-r--r-- 1 root root   15792 2007-05-16 13:06 libkrb5support.so.0
-rw-r--r-- 1 root root   89512 2007-05-16 13:06 libz.so.1
drwxr-xr-x 2 root root    4096 2007-05-16 13:06 openssh
drwxr-xr-x 2 root root    4096 2007-05-16 13:06 rssh
lrwxrwxrwx 1 root root      45 2007-05-17 10:55 sftp-server -> /usr/local/chroot/usr/lib/openssh/sftp-server

/usr/local/chroot/usr/lib/openssh:
total 40
-rwxr-xr-x 1 root root 36992 2007-05-16 13:06 sftp-server

/usr/local/chroot/usr/lib/rssh:
total 24
-rwsr-xr-x 1 root root 23624 2007-05-16 13:06 rssh_chroot_helper


``` 

I get connection closed when trying with sftp or scp.  As far as I can see the 2 files mentioned below are present and executable!?

```

May 17 11:18:41 delia rssh[8474]: setting log facility to LOG_USER
May 17 11:18:41 delia rssh[8474]: allowing scp to all users
May 17 11:18:41 delia rssh[8474]: allowing sftp to all users
May 17 11:18:41 delia rssh[8474]: setting umask to 022
May 17 11:18:41 delia rssh[8474]: chrooting all users to /usr/local/chroot
May 17 11:18:41 delia rssh[8474]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 1 "scp -t me.txt"
May 17 11:18:41 delia rssh_chroot_helper[8474]: new session for cheers, UID=1005
May 17 11:18:41 delia rssh_chroot_helper[8474]: user's home dir is /usr/local/chroot/home/cheers
May 17 11:18:41 delia rssh_chroot_helper[8474]: chrooted to /usr/local/chroot
May 17 11:18:41 delia rssh_chroot_helper[8474]: changing working directory to /home/cheers (inside jail)
May 17 11:18:41 delia rssh_chroot_helper[8474]: execv() failed, /usr/bin/scp: No such file or directory

```
 or : 

```

May 17 11:12:02 delia rssh[8401]: allowing scp to all users
May 17 11:12:02 delia rssh[8401]: allowing sftp to all users
May 17 11:12:02 delia rssh[8401]: setting umask to 022
May 17 11:12:02 delia rssh[8401]: chrooting all users to /usr/local/chroot
May 17 11:12:02 delia rssh[8401]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
May 17 11:12:02 delia rssh_chroot_helper[8401]: new session for cheers, UID=1005
May 17 11:12:02 delia rssh_chroot_helper[8401]: user's home dir is /usr/local/chroot/home/cheers
May 17 11:12:02 delia rssh_chroot_helper[8401]: chrooted to /usr/local/chroot
May 17 11:12:02 delia rssh_chroot_helper[8401]: changing working directory to /home/cheers (inside jail)
May 17 11:12:02 delia rssh_chroot_helper[8401]: execv() failed, /usr/lib/openssh/sftp-server: No such file or directory


```

*any* help would be greatly appreciated.  ](*,)

---

### Post by reech on 2007-05-17
To get rssh working on dapper amd64 I did the following :

I added the following lines to the already modified mkchroot.sh script:

-------------snip-----------
```

#####################################################################
#
# set up /dev/log
#
mkdir -p "$jail_dir/dev"

######### user added code ##############
# cp some more files
cp /lib/ld-linux-x86-64.so.2 "$jail_dir/lib/"
cp /lib/ld-linux.so.2 "$jail_dir/lib/"
cp -pR /lib64 "$jail_dir/"
# make /dev/null
mknod -m 666 "$jail_dir/dev/null" c 1 3
########## end user added code ############

echo -e "NOTE: you must MANUALLY edit your syslog rc script to start syslogd"

```
-------------snip-----------

..and once you've created the chroot directory , create the chroot user and their home.

Don't forget to restart sysklogd:

```

/etc/init.d/sysklogd restart

```

Hope that helps somebody.

---

### Post by jetpeach on 2007-06-06
I'm running Feisty and have spent a few hours following the guide, but cannot get it to work.
Here are the outputs to some commands, any help will be greatly appreciated, I'm quite frustrated now.

sftp -v -v sftp@localhost
after logging in, it takes the password correctly and continues, ending with
```
debug2: channel 0: input open -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 1
Connection closed
```

My sys log seems messed up, doesn't seem to be recording the sftp data giving only
sudo cat /var/log/syslog | tail -6
```
Jun  6 17:46:16 ubuntu rssh[9872]: setting log facility to LOG_USER
Jun  6 17:46:16 ubuntu rssh[9872]: allowing scp to all users
Jun  6 17:46:16 ubuntu rssh[9872]: allowing sftp to all users
Jun  6 17:46:16 ubuntu rssh[9872]: setting umask to 022
Jun  6 17:46:16 ubuntu rssh[9872]: chrooting all users to /home/chroot
```

ls -lR
```
.:
total 20
drwxr-xr-x 2 root root 4096 2007-06-06 17:42 dev
drwxr-xr-x 2 root root 4096 2007-06-06 17:23 etc
drwxr-xr-x 3 root root 4096 2007-06-06 16:53 home
drwxr-xr-x 3 root root 4096 2007-06-06 17:32 lib
drwxr-xr-x 4 root root 4096 2007-06-06 14:42 usr

./dev:
total 0
crw-rw-rw- 1 root root 1, 3 2007-06-06 17:42 null

./etc:
total 140
-rw-r--r-- 1 root root 119609 2007-06-06 16:50 ld.so.cache
-rw-r--r-- 1 root root     49 2007-06-06 16:50 ld.so.conf
-rw-r--r-- 1 root root    170 2007-06-06 16:50 ld.so.hwcappkgs
-rw-r--r-- 1 root root    503 2007-06-06 16:50 nsswitch.conf
-rw-r--r-- 1 root root     55 2007-06-06 17:24 passwd

./home:
total 4
drwxr-xr-x 2 sftp root 4096 2007-06-06 16:53 sftp

./home/sftp:
total 0

./lib:
total 232
-rwxr-xr-x 1 root root 109268 2007-06-06 14:45 ld-linux.so.2
-rw-r--r-- 1 root root   5792 2007-06-06 16:50 libcom_err.so.2
-rw-r--r-- 1 root root  26340 2007-04-04 03:48 libnss_compat-2.5.so
lrwxrwxrwx 1 root root     20 2007-06-06 16:50 libnss_compat.so.2 -> libnss_compat-2.5.so
-rw-r--r-- 1 root root  34320 2007-04-04 03:48 libnss_files-2.5.so
lrwxrwxrwx 1 root root     19 2007-06-06 16:50 libnss_files.so.2 -> libnss_files-2.5.so
-rwxr-xr-x 1 root root  43244 2007-06-06 17:32 sftp-server
drwxr-xr-x 3 root root   4096 2007-06-06 14:44 tls

./lib/tls:
total 4
drwxr-xr-x 3 root root 4096 2007-06-06 14:44 i686

./lib/tls/i686:
total 4
drwxr-xr-x 2 root root 4096 2007-06-06 14:44 cmov

./lib/tls/i686/cmov:
total 1488
-rw-r--r-- 1 root root   21908 2007-06-06 16:50 libcrypt.so.1
-rw-r--r-- 1 root root 1307104 2007-06-06 16:50 libc.so.6
-rw-r--r-- 1 root root    9684 2007-06-06 16:50 libdl.so.2
-rw-r--r-- 1 root root   79596 2007-06-06 16:50 libnsl.so.1
-rw-r--r-- 1 root root   67408 2007-06-06 16:50 libresolv.so.2
-rw-r--r-- 1 root root    9696 2007-06-06 16:50 libutil.so.1

./usr:
total 8
drwxr-xr-x 2 root root 4096 2007-06-06 14:44 bin
drwxr-xr-x 5 root root 4096 2007-06-06 17:44 lib

./usr/bin:
total 68
-rwxr-xr-x 1 root root 19332 2007-06-06 16:50 rssh
-rwxr-xr-x 1 root root 48940 2007-06-06 16:50 scp

./usr/lib:
total 980
drwxr-xr-x 3 root root   4096 2007-06-06 14:44 i686
-rw-r--r-- 1 root root 113800 2007-06-06 16:50 libgssapi_krb5.so.2
-rw-r--r-- 1 root root 151296 2007-06-06 16:50 libk5crypto.so.3
-rw-r--r-- 1 root root 512500 2007-06-06 16:50 libkrb5.so.3
-rw-r--r-- 1 root root  14164 2007-06-06 16:50 libkrb5support.so.0
-rw-r--r-- 1 root root  78276 2007-06-06 16:50 libz.so.1
drwxr-xr-x 2 root root   4096 2007-06-06 14:42 openssh
drwxr-xr-x 2 root root   4096 2007-06-06 14:44 rssh
-rwxr-xr-x 1 root root  48940 2007-06-06 17:44 scp
-rwxr-xr-x 2 root root  43244 2007-06-06 16:50 sftp-server

./usr/lib/i686:
total 4
drwxr-xr-x 2 root root 4096 2007-06-06 14:44 cmov

./usr/lib/i686/cmov:
total 1276
-rw-r--r-- 1 root root 1299428 2007-06-06 16:50 libcrypto.so.0.9.8

./usr/lib/openssh:
total 44
-rwxr-xr-x 2 root root 43244 2007-06-06 16:50 sftp-server

./usr/lib/rssh:
total 20
-rwsr-xr-x 1 root root 18740 2007-06-06 16:50 rssh_chroot_helper
```

cat /etc/rssh.conf
```
# This is the default rssh config file

# set the log facility.  "LOG_USER" and "user" are equivalent.
logfacility = LOG_USER

# Leave these all commented out to make the default action for rssh to lock
# users out completely...

allowscp
allowsftp
#allowcvs
#allowrdist
#allowrsync

# set the default umask
umask = 022

# If you want to chroot users, use this to set the directory where the root of
# the chroot jail will be located.
#
# if you DO NOT want to chroot users, LEAVE THIS COMMENTED OUT.
# chrootpath = /usr/local/chroot

chrootpath = "/home/chroot"

##########################################
# EXAMPLES of configuring per-user options

#user=rudy:077:00010:  # the path can simply be left out to not chroot
#user=rudy:077:00010   # the ending colon is optional

#user=rudy:011:00100:  # cvs, with no chroot
#user=rudy:011:01000:  # rdist, with no chroot
#user=rudy:011:10000:  # rsync, with no chroot
#user="rudy:011:00001:/usr/local/chroot"  # whole user string can be quoted
#user=rudy:01"1:00001:/usr/local/chroot"  # or somewhere in the middle, freak!
#user=rudy:'011:00001:/usr/local/chroot'  # single quotes too

# if your chroot_path contains spaces, it must be quoted...
# In the following examples, the chroot_path is "/usr/local/my chroot"
#user=rudy:011:00001:"/usr/local/my chroot"  # scp with chroot
#user=rudy:011:00010:"/usr/local/my chroot"  # sftp with chroot
#user=rudy:011:00011:"/usr/local/my chroot"  # both with chroot

# Spaces before or after the '=' are fine, but spaces in chrootpath need
# quotes.
#user = "rudy:011:00001:/usr/local/my chroot"
#user = "rudy:011:00001:/usr/local/my chroot"  # neither do comments at line end

```

Thanks for any help!

---

### Post by jetpeach on 2007-06-08
i fixed my problem but don't know why i needed to do what i did - i was looking at another guide to set this up
[http://ubuntuforums.org/showthread.php?t=248724&highlight=chroot](http://ubuntuforums.org/showthread.php?t=248724&highlight=chroot)
and saw that he said to do put bashrc in and chown the chroot home jail, using commands like these but replacing with your junk...

chown thomas:thomas /jail/home/thomas
sudo cp /home/trawler/.bashrc /jail/home/thomas
sudo chown thomas:thomas /jail/home/thomas/.bashrc

after doing this, i looged in with ssh and it works for me. asked me to change my password but then works and same with sftp.  whew, finally!

EDIT: strangely, i tried deleting the .bashrc file now and it works, i'm not sure what was messed up, but glad it's over

---

### Post by skiddex on 2007-07-02
Hi, this guide is great but I am still running into some problems, here is the output when trying to sftp to localhost:

```

root@xeonfs:/file_server# sftp bbullard@localhost
Connecting to localhost...
bbullard@localhost's password: 
Permission denied, please try again.
bbullard@localhost's password: 
root@xeonfs:/file_server# sftp -v bbullard@localhost
Connecting to localhost...
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
bbullard@localhost's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending subsystem: sftp
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 1
Connection closed

```

here is hopefully the information that will help.

I am trying to jail in /file_server

File structure: 

```

root@xeonfs:/file_server# ls -l
total 160
drwxrwxrwx 2 root root   4096 2007-06-30 17:33 dev
drwxrwxrwx 5 root root   4096 2007-06-26 21:48 downloads
drwxrwxrwx 2 root root   4096 2007-06-30 17:33 etc
-rwxrwxrwx 1 root root 109268 2007-06-30 17:35 ld-linux.so.2
drwxrwxrwx 3 root root   4096 2007-06-30 17:57 lib
drwxrwxrwx 2 root root  16384 2007-06-25 23:43 lost+found
drwxrwxrwx 5 root root   4096 2007-07-02 13:09 private
drwxrwxrwx 6 root root   4096 2007-07-02 09:36 public
drwxrwxrwx 3 root root   4096 2007-06-26 17:42 upload
drwxrwxrwx 4 root root   4096 2007-06-30 17:33 usr

root@xeonfs:/file_server/usr# ls -Rl
.:
total 8
drwxrwxrwx 2 root root 4096 2007-06-30 17:33 bin
drwxrwxrwx 5 root root 4096 2007-06-30 17:48 lib

./bin:
total 68
-rwxrwxrwx 1 root root 19332 2007-06-30 17:33 rssh
-rwxrwxrwx 1 root root 48940 2007-06-30 17:33 scp

./lib:
total 932
drwxrwxrwx 3 root root   4096 2007-06-30 17:33 i686
-rwxrwxrwx 1 root root 113800 2007-06-30 17:33 libgssapi_krb5.so.2
-rwxrwxrwx 1 root root 151296 2007-06-30 17:33 libk5crypto.so.3
-rwxrwxrwx 1 root root 512500 2007-06-30 17:33 libkrb5.so.3
-rwxrwxrwx 1 root root  14164 2007-06-30 17:33 libkrb5support.so.0
-rwxrwxrwx 1 root root  78276 2007-06-30 17:33 libz.so.1
drwxrwxrwx 2 root root   4096 2007-06-30 17:33 openssh
drwxrwxrwx 2 root root   4096 2007-06-30 17:33 rssh
-rwxrwxrwx 2 root root  43244 2007-06-30 17:33 sftp-server

./lib/i686:
total 4
drwxrwxrwx 2 root root 4096 2007-06-30 17:33 cmov

./lib/i686/cmov:
total 1276
-rwxrwxrwx 1 root root 1299428 2007-06-30 17:33 libcrypto.so.0.9.8

./lib/openssh:
total 44
-rwxrwxrwx 2 root root 43244 2007-06-30 17:33 sftp-server

./lib/rssh:
total 20
-rwxrwxrwx 1 root root 18740 2007-06-30 17:33 rssh_chroot_helper

root@xeonfs:/file_server/dev# ls -Rla
.:
total 8
drwxrwxrwx  2 root root 4096 2007-06-30 17:33 .
drwxrwxrwx 11 root root 4096 2007-07-02 09:22 ..

root@xeonfs:/file_server/etc# ls -Rl
.:
total 56
-rwxrwxrwx 1 root root 38916 2007-06-30 17:33 ld.so.cache
-rwxrwxrwx 1 root root    33 2007-06-30 17:33 ld.so.conf
-rwxrwxrwx 1 root root    45 2007-06-30 17:33 ld.so.hwcappkgs
-rwxrwxrwx 1 root root   513 2007-06-30 17:33 nsswitch.conf
-rwxrwxrwx 1 root root  1488 2007-06-30 17:33 passwd

root@xeonfs:/file_server/lib# ls -lRa
.:
total 196
drwxrwxrwx  3 root root   4096 2007-06-30 17:57 .
drwxrwxrwx 11 root root   4096 2007-07-02 09:22 ..
-rwxrwxrwx  1 root root 109268 2007-06-30 17:57 ld-linux.so.2
-rwxrwxrwx  1 root root   5792 2007-06-30 17:33 libcom_err.so.2
-rwxrwxrwx  1 root root  26340 2007-06-30 17:35 libnss_compat-2.5.so
lrwxrwxrwx  1 root root     20 2007-06-30 17:33 libnss_compat.so.2 -> libnss_compat-2.5.so
-rwxrwxrwx  1 root root  34320 2007-04-04 05:48 libnss_files-2.5.so
lrwxrwxrwx  1 root root     19 2007-06-30 17:33 libnss_files.so.2 -> libnss_files-2.5.so
drwxrwxrwx  3 root root   4096 2007-06-30 17:33 tls

./tls:
total 12
drwxrwxrwx 3 root root 4096 2007-06-30 17:33 .
drwxrwxrwx 3 root root 4096 2007-06-30 17:57 ..
drwxrwxrwx 3 root root 4096 2007-06-30 17:33 i686

./tls/i686:
total 12
drwxrwxrwx 3 root root 4096 2007-06-30 17:33 .
drwxrwxrwx 3 root root 4096 2007-06-30 17:33 ..
drwxrwxrwx 2 root root 4096 2007-06-30 17:33 cmov

./tls/i686/cmov:
total 1496
drwxrwxrwx 2 root root    4096 2007-06-30 17:33 .
drwxrwxrwx 3 root root    4096 2007-06-30 17:33 ..
-rwxrwxrwx 1 root root   21908 2007-06-30 17:33 libcrypt.so.1
-rwxrwxrwx 1 root root 1307104 2007-06-30 17:33 libc.so.6
-rwxrwxrwx 1 root root    9684 2007-06-30 17:33 libdl.so.2
-rwxrwxrwx 1 root root   79596 2007-06-30 17:33 libnsl.so.1
-rwxrwxrwx 1 root root   67408 2007-06-30 17:33 libresolv.so.2
-rwxrwxrwx 1 root root    9696 2007-06-30 17:33 libutil.so.1
root@xeonfs:/file_server/lib# ls -lR
.:
total 188
-rwxrwxrwx 1 root root 109268 2007-06-30 17:57 ld-linux.so.2
-rwxrwxrwx 1 root root   5792 2007-06-30 17:33 libcom_err.so.2
-rwxrwxrwx 1 root root  26340 2007-06-30 17:35 libnss_compat-2.5.so
lrwxrwxrwx 1 root root     20 2007-06-30 17:33 libnss_compat.so.2 -> libnss_compat-2.5.so
-rwxrwxrwx 1 root root  34320 2007-04-04 05:48 libnss_files-2.5.so
lrwxrwxrwx 1 root root     19 2007-06-30 17:33 libnss_files.so.2 -> libnss_files-2.5.so
drwxrwxrwx 3 root root   4096 2007-06-30 17:33 tls

./tls:
total 4
drwxrwxrwx 3 root root 4096 2007-06-30 17:33 i686

./tls/i686:
total 4
drwxrwxrwx 2 root root 4096 2007-06-30 17:33 cmov

./tls/i686/cmov:
total 1488
-rwxrwxrwx 1 root root   21908 2007-06-30 17:33 libcrypt.so.1
-rwxrwxrwx 1 root root 1307104 2007-06-30 17:33 libc.so.6
-rwxrwxrwx 1 root root    9684 2007-06-30 17:33 libdl.so.2
-rwxrwxrwx 1 root root   79596 2007-06-30 17:33 libnsl.so.1
-rwxrwxrwx 1 root root   67408 2007-06-30 17:33 libresolv.so.2
-rwxrwxrwx 1 root root    9696 2007-06-30 17:33 libutil.so.1

```

syslog
```

root@xeonfs:/file_server/lib# cat /var/log/syslog | tail -7
Jul  2 14:10:23 xeonfs rssh[26450]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
Jul  2 14:17:02 xeonfs /USR/SBIN/CRON[26554]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 14:17:47 xeonfs rssh[26574]: setting log facility to LOG_USER
Jul  2 14:17:47 xeonfs rssh[26574]: allowing sftp to all users
Jul  2 14:17:47 xeonfs rssh[26574]: setting umask to 022
Jul  2 14:17:47 xeonfs rssh[26574]: chrooting all users to /file_server
Jul  2 14:17:47 xeonfs rssh[26574]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"

```

/etc/rssh.conf
```

root@xeonfs:/etc# cat rssh.conf
# This is the default rssh config file

# set the log facility.  "LOG_USER" and "user" are equivalent.
logfacility = LOG_USER 

# Leave these all commented out to make the default action for rssh to lock
# users out completely...

#allowscp
allowsftp
#allowcvs
#allowrdist
#allowrsync

# set the default umask
umask = 022

# If you want to chroot users, use this to set the directory where the root of
# the chroot jail will be located.
#
# if you DO NOT want to chroot users, LEAVE THIS COMMENTED OUT.
# chrootpath = /usr/local/chroot

# You can quote anywhere, but quotes not required unless the path contains a
# space... as in this example.
# chrootpath = "/usr/local/my chroot"
chrootpath = /file_server

##########################################
# EXAMPLES of configuring per-user options

#user=rudy:077:00010:  # the path can simply be left out to not chroot
#user=rudy:077:00010   # the ending colon is optional

#user=rudy:011:00100:  # cvs, with no chroot 
#user=rudy:011:01000:  # rdist, with no chroot
#user=rudy:011:10000:  # rsync, with no chroot
#user="rudy:011:00001:/usr/local/chroot"  # whole user string can be quoted
#user=rudy:01"1:00001:/usr/local/chroot"  # or somewhere in the middle, freak!
#user=rudy:'011:00001:/usr/local/chroot'  # single quotes too

# if your chroot_path contains spaces, it must be quoted...
# In the following examples, the chroot_path is "/usr/local/my chroot"
#user=rudy:011:00001:"/usr/local/my chroot"  # scp with chroot
#user=rudy:011:00010:"/usr/local/my chroot"  # sftp with chroot
#user=rudy:011:00011:"/usr/local/my chroot"  # both with chroot

# Spaces before or after the '=' are fine, but spaces in chrootpath need
# quotes.
#user = "rudy:011:00001:/usr/local/my chroot"  
#user = "rudy:011:00001:/usr/local/my chroot"  # neither do comments at line end

```

Any help greatly appreciated! Its probably something simple and stupid on my part

---

### Post by cdukes on 2007-09-11
I got everything working (using Feisty)
Note that the nss library should be compat (not compact)
My question:
Can I allow access to a directory OUTSIDE the chroot jail? It's mounted on another disk.
I tried the obvious, creating a sym link, but no dice.
Anyone know if this can be done?

---

### Post by jchau on 2007-09-11
> **cdukes said:**
> I got everything working (using Feisty)
Note that the nss library should be compat (not compact)
My question:
Can I allow access to a directory OUTSIDE the chroot jail? It's mounted on another disk.
I tried the obvious, creating a sym link, but no dice.
Anyone know if this can be done?

Thanks for the correction, the howto has been updated accordingly.  

There _should not_ be any way to to access a file outside of the chroot jail.  If it were on the same partition, you could create a hard link to include something in the chroot jail (because it will actually be in the chroot jail).  Hard links cannot be made across different partitions.  

A symbolic link will not do the trick since it is just a file storing the path to the actual file instead of the actual file, which isn't accessible since it is outside the jail.  Also, if people were able to use symbolic links to escape the jail, anyone will be able to escape the jail by uploading their own symbolic links.  

If you really want to do this though, you can try mounting the disk to a directory within the chroot jail and then create a symbolic link at the original mount-point to the new mount-point.  I haven't tried this though so I'm not sure if this works.  There are probably other ways too.  

Good luck.  

BTW, apologies to anyone who I haven't replied to.  I no longer have Ubuntu installed so I can't experiment to find solutions your problems.

---

### Post by cdukes on 2007-09-11
Thanks, I'll give that a shot :-)
Curious -- why the switch from Ubuntu? What are you running now?

---

### Post by cdukes on 2007-09-11
Mounting it under /home/chroot did the trick, thanks a ton!

---

### Post by hausmaus on 2007-10-25
Though I'm not using Ubuntu (but CentOS for the server) this tutorial helped a lot, before I found it nothing worked. Thanks :-) 

I've got still one problem, wenn I start the sftp to my server I get the following errors in /var/log/messages:

```

Oct 25 17:25:22 myserver rssh[17388]: setting log facility to LOG_USER
Oct 25 17:25:22 myserver rssh[17388]: allowing sftp to all users
Oct 25 17:25:22 myserver rssh[17388]: setting umask to 022
Oct 25 17:25:22 myserver rssh[17388]: line 31: configuring user test
Oct 25 17:25:22 myserver rssh[17388]: setting test's umask to 022
Oct 25 17:25:22 myserver rssh[17388]: allowing sftp to user test
Oct 25 17:25:22 myserver rssh[17388]: chrooting test to /var/chroot
Oct 25 17:25:22 myserver rssh[17388]: chroot cmd line: /usr/libexec/rssh_chroot_helper 2 "/usr/libexec/openssh/sftp-server"
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: new session for test, UID=505
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: user's home dir is /home/test
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: couldn't find /home/test in chroot jail
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: chrooted to /var/chroot
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: changing working directory to / (inside jail)


```

The jail is configured in /var/chroot/, but I don't think that matters... The directories /home/test and /var/chroot/home/test exist, the permissions are set just as in the "normal" /home-dir.

I can log in, but start in the root of the chroot-jail. From there I can normally cd into the home directory of the user. 

What could be wrong? :redface:


Daniela

---

### Post by rgeddes on 2007-10-26
I followed the directions for this how-to and with few problems, managed to get it working about 2 months ago on Fiesty.  Upgraded to Gutsy and remote connections were being closed at login.  I tried to access their accounts through sftp using my public ip address and was rejected:

/var/log/user.log showed:
```
Oct 26 16:39:53 rg-desktop rssh_chroot_helper[28408]: chroot() failed, 2: Operation not permitted
```

Anyway, going over the steps for setup, I discovered the following step was reversed after the upgrade:
```
 sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper
```

After re-executing the command, I could successfully sftp into that chrooted account, albeit from the same machine....  which I couldn't do before.

I think it would have taken much longer to find this problem without the how-to.

Thnx

PS... Does it sound correct that the upgrade from Fiesty to Gutsy would modify the file attribute for /usr/lib/rssh/rssh_chroot_helper?  If yes, why?

---

### Post by rgeddes on 2007-10-26
> **hausmaus said:**
> Though I'm not using Ubuntu (but CentOS for the server) this tutorial helped a lot, before I found it nothing worked. Thanks :-) 

I've got still one problem, wenn I start the sftp to my server I get the following errors in /var/log/messages:

```

Oct 25 17:25:22 myserver rssh[17388]: setting log facility to LOG_USER
Oct 25 17:25:22 myserver rssh[17388]: allowing sftp to all users
Oct 25 17:25:22 myserver rssh[17388]: setting umask to 022
Oct 25 17:25:22 myserver rssh[17388]: line 31: configuring user test
Oct 25 17:25:22 myserver rssh[17388]: setting test's umask to 022
Oct 25 17:25:22 myserver rssh[17388]: allowing sftp to user test
Oct 25 17:25:22 myserver rssh[17388]: chrooting test to /var/chroot
Oct 25 17:25:22 myserver rssh[17388]: chroot cmd line: /usr/libexec/rssh_chroot_helper 2 "/usr/libexec/openssh/sftp-server"
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: new session for test, UID=505
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: user's home dir is /home/test
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: couldn't find /home/test in chroot jail
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: chrooted to /var/chroot
Oct 25 15:25:22 myserver rssh_chroot_helper[17388]: changing working directory to / (inside jail)


```

The jail is configured in /var/chroot/, but I don't think that matters... The directories /home/test and /var/chroot/home/test exist, the permissions are set just as in the "normal" /home-dir.

I can log in, but start in the root of the chroot-jail. From there I can normally cd into the home directory of the user. 

What could be wrong? :redface:


Daniela

It looks like rssh_chroot_helper doesn't know the chroot 'root' directory or the directory it's looking for, is not in the chroot root directory.

A successful chrooted sftp connection looks like this on my machine:
```
Oct 26 17:02:10 rg-desktop rssh[28888]: allowing sftp to all users
Oct 26 17:02:10 rg-desktop rssh[28888]: setting umask to 022
Oct 26 17:02:10 rg-desktop rssh[28888]: chrooting all users to /home/chroot
Oct 26 17:02:10 rg-desktop rssh[28888]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```
In your log there is an error message about not finding /home/test in the chroot jail.  The chroot jail, I believe, is the chroot root... ie it's a directory that acts as the root (can't access any parent directories) for chrooted connections.  

So either the directory /home/test isn't under the chroot jail directory or the chroot jail directory isn't identified properly.

In my system chroot root is /home/chroot and the home directories are listed under that directory... eg to grant 'userabc' chrooted access, set his/her home directory to /home/chroot/home/userabc.  

This is the way this howto presents the material... of course you could use a different directory as your chroot root directory.. but if you're getting used to the lingo and buzzwords... keep it simple and follow the steps... eventually the lingo and buzzwords will not be as distracting, and you can make detours more easily.

---

### Post by hausmaus on 2007-10-29
@rgeddes

Thanks, I simply forgot to set the homedir correctly in the "real" /etc/passwd, it was only set in the /var/chroot/etc/passwd...  ](*,) 
It works! :-D

Sorry for stealing your time with my stupidity...  :oops:

Daniela

---

### Post by debubun on 2007-10-29
hi all,
first thanks for this how-to ;)
Well, there's someting still not clear for me, concerning syslog.

Some have on their chroot directory a dev/log file which is of socket type ?
(i think i see it on page 2 or maybe 3).
Is it required ?

Following  this how-to, we should put SYSLOGD= in /etc/init.d/syslogd to -a /pathtochroot/dev/log. What is the log file type ? 
As we have "all" /var/log/syslog on our system, that is a simple file where syslog writes, is /pathtochroot/dev/log a simple file too ? 

I wonder that cause when i log via sftp on a remote host well configured, syslog write on /var/log/syslog, that is normal. But when i sftp some file to this remote host, there's no trace of that either in /var/log/syslog nor /pathtochroot/dev/log (when log is a simple file rw for all users).

What is the problem with that ?

ps:some personnal remarques:
1/  i think it's quite essential to mknod /pathtochrrot/dev/null c 1 3 to avoid a "connection close" that 've been drivin' me mad for a week :( trying to connect.
As we can see on syslog someting like : 
```
'chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"'
```
if we try to run this command on a terminal : 
```
# /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
```
and we get something like "can't open /dev/null on /pathtochroot/dev ... no such file ... " all becomes clear.

2/ i still don't understand how to choose minor/major code on the mknod command. I set them to 1 3 just because i've been seen that elsewhere ... but stil wondering ...

3/ scuse me for my bad english sometimes ... frenchy guy i am. ;)

4/ i will start again from 0 to see if mkchroot.sh (with some basic modifications) works correctly on x86_64 (i am running debian x86_64). Just to make sure that my problem with "conection close" is only due to /pathtochroot/dev/null, and not the missing of some librairies ..

---

### Post by jalla2000 on 2007-10-31
Can anyone of you elite linux ppl tell me why it doesn't work for me? I am running ubuntu 7.04 gutsy

jalla@tullepc:~$ sftp -vv [email]sftptest@myhost.no[/email]
Connecting to myhost.no...
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to myhost.no [129.241.205.179] port 22.
debug1: Connection established.
debug1: identity file /home/jalla/.ssh/id_rsa type -1
debug1: identity file /home/jalla/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5build1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 121/256
debug2: bits set: 521/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'myhost.no' is known and matches the RSA host key.
debug1: Found key in /home/jalla/.ssh/known_hosts:4
debug2: bits set: 489/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/jalla/.ssh/id_rsa ((nil))
debug2: key: /home/jalla/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jalla/.ssh/id_rsa
debug1: Trying private key: /home/jalla/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
[email]sftptest@myhost.no[/email]'s password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug2: fd 4 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 131072
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 0
Connection closed

---

### Post by me1on on 2007-11-01
I'm hoping someone can help me; it's probably a stupid mistake, but I get a "Permission denied" error when I try to log in. :( Here's the output:
```
me1on@me1on:~$ sftp -v -v -oPort=35731 sft@localhost
Connecting to localhost...
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 35731.
debug1: Connection established.
debug1: identity file /home/me1on/.ssh/id_rsa type -1
debug1: identity file /home/me1on/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5build1
debug1: match: OpenSSH_4.6p1 Debian-5build1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5build1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 133/256
debug2: bits set: 510/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: checking without port identifier
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/me1on/.ssh/known_hosts:3
debug1: found matching key w/out port
debug2: bits set: 511/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/me1on/.ssh/id_rsa ((nil))
debug2: key: /home/me1on/.ssh/id_dsa ((nil))
               __
              /_ |
 _ __ ___   ___| | ___  _ __
| '_ ` _ \ / _ \ |/ _ \| '_ \
| | | | | |  __/ | (_) | | | |
|_| |_| |_|\___|_|\___/|_| |_|

Welcome to me1on's SSH server.
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/me1on/.ssh/id_rsa
debug1: Trying private key: /home/me1on/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
sft@localhost's password:
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
sft@localhost's password:    
```

I'm sure I entered the correct password though, as I can use the same password to log into the "sft" account on my computer. Is it possible for the "sft" user to have a different password for ssh than it does for local logins?

EDIT: Solved! In my sshd_config, I had a line that said "AllowUsers me1on", which I had to change to "AllowUsers me1on sft"

---

### Post by zax123 on 2007-11-02
Please help...

I had this working perfect in Edgy, but I've upgraded to Gutsy now using Ubuntu's upgrade function.

All my chroot'ed users cannot login.  The auth.log shows this error:

Nov  2 09:17:42 localhost sshd[5895]: pam_unix(ssh:session): session opened for user testme by (uid=0)
Nov  2 09:17:42 localhost sshd[5895]: pam_env(ssh:setcred): Unable to open config file: /etc/security/pam_env.conf: No such file or directory
Nov  2 09:17:42 localhost sshd[5895]: fatal: ssh_selinux_getctxbyname: ssh_selinux_getctxbyname: security_getenforce() failed

Does anyone have any idea what this means?

Please help if you can.

Thanks!

Rob

---

### Post by talen.quickblade on 2007-11-24
> **edylie said:**
>  ...for those getting the connection closed message, make sure you have null in your /home/chroot/dev directory

if it does not exist, excute the following command

sudo mknod -m 666 /home/chroot/dev/null c 1 3

w00t!!

This did it for me...
now I need to pick back through this so I can do it again later if I need to. not to mention cleaning up the trail of junk I left in my wake as I tried to narrow down the problem.

Thanks for the howto, and thanks for the help!

---

### Post by dehappy on 2007-11-28
An FYI to any 64-bit users - remember to copy the appropriate **_lib64_** libs into the jail, too!  ](*,)

Otherwise, *rssh_chroot_helper* won't be able to start *sftp-server*.  From my syslog:

[I]Nov 28 14:55:40 servername rssh_chroot_helper[3368]: execv() failed, /usr/lib/openssh/sftp-server: No such file or directory
[/I]
Hope that helps!

---

### Post by mac-duff on 2008-01-31
Hi,
nice tutorial but I receive one mistake. After I changed the startup script I can not login via ssh, (good) but neither via WinSCP. I guess there is somewhere a mistake but I dont know where ;)
Do u have some ideas?

SSH:
scp@192.168.68.137's password: 
Linux debian 2.6.18-5-686 #1 SMP Mon Dec 24 16:41:07 UTC 2007 i686

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Thu Jan 31 17:47:21 2008 from 192.168.68.1

This account is restricted by rssh.
Allowed commands: scp sftp 

If you believe this is in error, please contact your system administrator.

Connection to 192.168.68.137 closed.


WinSCP:
Cannot initialize SFTP protocol. Is the host running a SFTP server?

---

### Post by onizuka-21 on 2008-02-05
Hi

Just like most people here, after going through the tutorial i got rejected while trying to sftp to the server (Connection closed.) 

I've been trying a bunch of different things for several days, and it finally works. The problem was : the mknod command is not stated clearly enough on the first post. As mentionned earlier by someone else, the nod must be
/home/chroot/dev/null

instead of 
mknod -m 666 /home/chroot/dir/dev/null c 1 3

from the first post.

Perhaps you could change that, or explain to me where I am wrong.

Anyway thank you for the great tutorial, I keep thinking such a feature should be set by default on linux server installs, but as it is not it's really nice to have such good tutorials. :)

Cheers

---

### Post by jchau on 2008-02-05
Thanks.  I don't know how that mistake was made, but it's fixed now.  

> **onizuka-21 said:**
> Hi

Just like most people here, after going through the tutorial i got rejected while trying to sftp to the server (Connection closed.) 

I've been trying a bunch of different things for several days, and it finally works. The problem was : the mknod command is not stated clearly enough on the first post. As mentionned earlier by someone else, the nod must be
/home/chroot/dev/null

instead of 
mknod -m 666 /home/chroot/dir/dev/null c 1 3

from the first post.

Perhaps you could change that, or explain to me where I am wrong.

Anyway thank you for the great tutorial, I keep thinking such a feature should be set by default on linux server installs, but as it is not it's really nice to have such good tutorials. :)

Cheers

---

### Post by JGZimmerle on 2008-02-07
Hi!

Edit: got it working after all.

---

### Post by FreeStyling on 2008-02-26
> **aprita said:**
> 
*** glibc detected *** -rssh: malloc(): memory corruption: 0x0804fc78 ***
======= Backtrace: =========
...
======= Memory map: ========
...
Connection to **** closed.



If you get the above error message when you try to SSH in then try commenting the "logfacility = LOG_USER" line in the  /etc/rssh.conf, alternatively try changing it to:

```
logfacility = user
```

When RSSH users login via ssh RSSH prints the message telling them that they are not allowed to login then logs the attempt before exiting, therefore something in the logging is the most likely cause of the problem described on page 3.

---

### Post by mtegmont on 2008-03-12
[COLOR="Red"]**UPDATE! UPDATE!**

DO NOT suid the chroot rssh_chroot_helper. This gives sftp users root privileges in the chroot environment!

I ended up not following this guide and found a way to patch openssh-server with the new sftp-chroot patch which makes all this a WHOLE LOT EASIER.

Excellent guide on patching openssh-server here:

[http://zephid.dk/2007/11/20/getting-the-power-of-sftp-chroot-in-debian/]("http://zephid.dk/2007/11/20/getting-the-power-of-sftp-chroot-in-debian/")

Thanks
[/COLOR]


Hi, many thanks for this guide.

I followed the instructions as closely as possible on Ubuntu 7.10.

But mine didn't work until doing this:

chmod u+s /home/chroot/usr/lib/rssh/rssh_chroot_helper

The guide only says to do this:

chmod u+s /usr/lib/rssh/rssh_chroot_helper

and seems to clarify that this is not meant to be done for the chroot environment.

I found that confusing, maybe I have read it wrong or done something else wrong but thats what i ended up needing for it to work.

Again, thanks for the rest of the guide, helped me a lot.



[I]From the original post:

In order for the chrooting process to work, "/usr/lib/rssh/rssh_chroot_helper" has to be setuid root. (Note: this path is relative to real root, not chroot root.) To setuid root, run the command:
Code:

sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper[/I]

---

### Post by jchau on 2008-03-13
> **mtegmont said:**
> Hi, many thanks for this guide.

I followed the instructions as closely as possible on Ubuntu 7.10.

But mine didn't work until doing this:

chmod u+s /home/chroot/usr/lib/rssh/rssh_chroot_helper

The guide only says to do this:

chmod u+s /usr/lib/rssh/rssh_chroot_helper

and seems to clarify that this is not meant to be done for the chroot environment.


Thanks for the suggestion.  At the time I wrote the guide, it was not necessary to allow /home/chroot/usr/lib/rssh/rssh_chroot_helper to run as root.  I am no longer running Ubuntu now, so I cannot confirm whether this is necessary now.  

However, I would advise **against** giving anything inside the chroot jail root privileges (as that chmod command would).  That would effectively defeat many layers of security.  If (through exploiting some bug), someone was able to break rssh, any SUID root file may become a shortcut to becoming root for the attacker.

---

### Post by mutineer612 on 2008-04-02
I am having similar issues with setting up CHROOT environment.  I get the following error in syslogd:

Apr  2 17:15:12 myhost rssh[4616]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
Apr  2 17:15:47 myhost rssh[4623]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"

RSSH shows sftp in the /openssh dir and symlink exists.  Also issues setuid cmd, with no change.    

rssh 2.3.2
sftp server binary = /usr/lib/openssh/sftp-server

Any thoughts?

---

### Post by ahome on 2008-05-03
Hi,

I have followed all the steps and it seems that everything works except that /home/chroot/etc/passwd file is not used, i.e. for login using rssh it is still used /etc/passwd.
My understanding is that only users from /home/chroot/etc/passwd should be able to login using sftp (ssh) isn't that the case?
If it is any idea what when wrong?

---

### Post by jchau on 2008-05-03
> **ahome said:**
> Hi,

I have followed all the steps and it seems that everything works except that /home/chroot/etc/passwd file is not used, i.e. for login using rssh it is still used /etc/passwd.
My understanding is that only users from /home/chroot/etc/passwd should be able to login using sftp (ssh) isn't that the case?
If it is any idea what when wrong?

That is NOT the case.  It's just that many programs expect to have /etc/passwd and if it's missing from the chroot jail, those programs may misbehave, so you put a copy of /etc/passwd there.  However, that copy isn't used for authentication.

---

### Post by ahome on 2008-05-04
Thank you very much. Do you know a way to enable rssh to only a sub-set of users, i.e. allow rssh only to one or two users out of all users regisered?

---

### Post by jchau on 2008-05-04
> **ahome said:**
> Thank you very much. Do you know a way to enable rssh to only a sub-set of users, i.e. allow rssh only to one or two users out of all users regisered?

You can have rssh disable rsync, rdist, cvs, sftp, and scp by default and then enable them for each user you want.  See the man page for rssh for more help (I don't have rssh ready to do testing right now).

---

### Post by ahome on 2008-05-06
that's good enough for now, thank you very much.

---

### Post by flamacue on 2008-07-13
Thanks for this guide.  I just used it to get a chrooted rssh server up on Gutsy (that is, Ubuntu 7.10).

I do have a couple questions, though.
> **mtegmont said:**
> [COLOR="Red"]**UPDATE! UPDATE!**

DO NOT suid the chroot rssh_chroot_helper. This gives sftp users root privileges in the chroot environment![/COLOR]
Looks to me like the guide says only to suid the *non*-chrooted rssh_chroot_helper, so that should alleviate this security concern, right?  Is there any security concern regarding doing suid on the non-chrooted rssh_chroot_helper, as the guide states?

For instance, what if I allow some chrooted and some non-chrooted users on my system, and maybe some of those non-chrooted users will have full ssh access.  Will the non-chrooted users be able to exploit the suid'd rssh_chroot_helper to escalate privileges?

> **mtegmont said:**
> [COLOR="Red"]I ended up not following this guide and found a way to patch openssh-server with the new sftp-chroot patch which makes all this a WHOLE LOT EASIER.

Excellent guide on patching openssh-server here:

[http://zephid.dk/2007/11/20/getting-the-power-of-sftp-chroot-in-debian/]("http://zephid.dk/2007/11/20/getting-the-power-of-sftp-chroot-in-debian/")

Thanks[/COLOR]
I'm not real fond of going to source, b/c then I'll miss out on any updates that Ubuntu makes for me.  :)  So, if the above situation that I describe is not a security concern, I think the best solution (for me) is to follow this guide.

...Interestingly, when I followed the [link]("http://zephid.dk/2007/11/20/getting-the-power-of-sftp-chroot-in-debian/") that mtegmont provided above, I found the following:

[quote=http://zephid.dk/2007/11/20/getting-the-power-of-sftp-chroot-in-debian/]I finally found a good solution, there is a patched version of OpenSSH which gives a chroot feature of making sftp only connections, this however does not allowed the user to use a shell also, it’s either sftp or ssh, not both, if you need this, you will have to create a chroot for every user.

[http://www.minstrel.org.uk/papers/sftp/](http://www.minstrel.org.uk/papers/sftp/)[/quote]

So I followed that link, and found the following:

[quote=http://www.minstrel.org.uk/papers/sftp/]Note: OpenSSH 4.9 now incorporates a built-in ability to chroot users (ChrootDirectory) and restrict them to SFTP (ForceCommand). I have started using this in my environment (instructions on how to do so can be found here), and so will no longer be keeping this page updated. I will leave it here, however, for those that are unable to upgrade to OpenSSH 4.9.[/quote]

So, it looks to me like an even better solution than this howto is on the horizon, once we get OpenSSH 4.9 in Ubuntu.  (Please someone correct me if I'm mistaken.)

However, it appears to me that even Hardy (Ubuntu 8.04) is [still using OpenSSH 4.7](http://packages.ubuntu.com/hardy/net/openssh-server).

I guess that's not surprising, though, since [OpenSSH 4.9 was only released on March 30, 2008](http://en.wikipedia.org/wiki/OpenSSH#History), which was not long before Hardy.  I suppose we'll see OpenSSH 5.0 (or later) in Intrepid (Ubuntu 8.10).

---

### Post by jchau on 2008-07-13
> **flamacue said:**
> Thanks for this guide.  I just used it to get a chrooted rssh server up on Gutsy (that is, Ubuntu 7.10).

I do have a couple questions, though.

Looks to me like the guide says only to suid the *non*-chrooted rssh_chroot_helper, so that should alleviate this security concern, right?  Is there any security concern regarding doing suid on the non-chrooted rssh_chroot_helper, as the guide states?

For instance, what if I allow some chrooted and some non-chrooted users on my system, and maybe some of those non-chrooted users will have full ssh access.  Will the non-chrooted users be able to exploit the suid'd rssh_chroot_helper to escalate privileges?

You're welcome.

Only suid root on the real rssh_chroot_helper (not the one in the chroot directory).  This is necessary because only the root user can chroot.  However, if a vulnerability is ever found in rssh_chroot_helper, this may still weaken your security against users who can run the real rssh_chroot_helper.  As an extra layer of security, you may want to ensure that only the users who are confined to the chroot jail have execute permission on rssh_chroot_helper.  

> **flamacue said:**
> So, it looks to me like an even better solution than this howto is on the horizon, once we get OpenSSH 4.9 in Ubuntu.  (Please someone correct me if I'm mistaken.)

However, it appears to me that even Hardy (Ubuntu 8.04) is [still using OpenSSH 4.7](http://packages.ubuntu.com/hardy/net/openssh-server).

I guess that's not surprising, though, since [OpenSSH 4.9 was only released on March 30, 2008](http://en.wikipedia.org/wiki/OpenSSH#History), which was not long before Hardy.  I suppose we'll see OpenSSH 5.0 (or later) in Intrepid (Ubuntu 8.10).

That's great news.  I eagerly await the better solution.  :-).

---

### Post by tha_toadman on 2008-09-13
Thanks for a great guide, jchau.

I'm having an issue though when I use WinSCP to connect to the server, via SFTP. I get the message

> Cannot initialize SFTP protocol. Is the host running a SFTP server?

I'm running it on 7.04 Server and I even followed the guide to the changing of the sftp-server into the openssh area. I restarted SSH and, at this point, I'm baffled as to what I may have missed? Any ideas?

---

### Post by jchau on 2008-09-13
> **tha_toadman said:**
> Thanks for a great guide, jchau.

I'm having an issue though when I use WinSCP to connect to the server, via SFTP. I get the message



I'm running it on 7.04 Server and I even followed the guide to the changing of the sftp-server into the openssh area. I restarted SSH and, at this point, I'm baffled as to what I may have missed? Any ideas?

What happens when you try ```
sftp localhost
``` on the computer running the server?

(Note that I haven't done this in a while.)

---

### Post by tha_toadman on 2008-09-13
That worked. Although I was on the server as 'root' and then I authenticated as 'root' and got a sftp> prompt.

I'll try as my user now and see what happens...and what it did was prompted me for a password, I must have authenticated but then PuTTY immediately died.

---

### Post by jchau on 2008-09-15
> **tha_toadman said:**
> That worked. Although I was on the server as 'root' and then I authenticated as 'root' and got a sftp> prompt.

I'll try as my user now and see what happens...and what it did was prompted me for a password, I must have authenticated but then PuTTY immediately died.

PuTTY?  Do you mean PSFTP?  rssh should prevent the rssh user from gaining a command shell, so it would be appropriate if the server killed your PuTTY session.

I would advise against using the root account for anything that doesn't absolutely require it.  That said, I don't think you should configure your ssh server to allow root to log in.  In the event that you do need to remotely access the root account, you should log into a normal account and use su or sudo to gain root instead.  The extra layer would prevent 
intruders from directly gaining root access to your computer.  

Also, testing the rssh setup with the root user is not helpful since I doubt that you set the root user's shell to rssh (if you did, you'd probably have other problems).  Try with an account configured to use rssh as the shell.

---

### Post by tha_toadman on 2008-09-17
> Also, testing the rssh setup with the root user is not helpful since I doubt that you set the root user's shell to rssh (if you did, you'd probably have other problems). Try with an account configured to use rssh as the shell.

Yes, and I agree. But that takes me to back to the guide that I followed and yet the user who was set with rssh, is what's causing this issue.

Is there a log that I should be looking at next?

---

### Post by GeirS73 on 2008-10-03
I had problems with sftp-server exiting due to missing libraries. I'm using the 64 bit 8.04 server version. My solution was as follows:

```

cp /usr/lib//ld-linux-x86-64.so.2 /home/chroot/usr/lib
ln -s /home/chroot/lib /home/chroot/lib64

```

Can't wait for OpenSSH 4.9 to show up :D
Thanks to jchau for a great posting and followups!

PS: I saw the other 64 bit postings too late, my apologies.

---

### Post by Wnutt on 2008-10-10
Hi folks,

I finally got it working ! :KS

Many thanks to Jchau for his howto and help !

And thanks to you all who posted your problems AND solutions.

That was very helpfull !

Fred

---

### Post by cypher35 on 2008-11-01
FYI, this is much easier now that the openssh package in Interpid is above version 4.8.

rssh is no longer necessary.

see: [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

### Post by fozzyuw on 2009-03-30
> **cypher35 said:**
> FYI, this is much easier now that the openssh package in Interpid is above version 4.8.

rssh is no longer necessary.

see: [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

Actually, it is easier to get chroot with OpenSSH 4.9+ (5.1 on Ubuntu 8.10), however, you cannot set umask using this method.

For whatever reason (I cannot seem to find why or a solution) the umask is always being set at the roots umask which is "umask 133" or "rw-r--r--".

I'm trying to get it to allow groups to write any files uploaded as well... "rw-rw-r--" or "umask 113".  However, I've googled several sources that have you making a script wrapper, or editing /etc/init.d/ssh to add the umask, etc.

I've yet to get one of those to work, so I'm trying this out.

My test case is transfering a txt file from windows using WinSCP to my Ubuntu box.  Every file I transfer ends up with "rw-r--r--".  Even when I "sudo touch somefile.txt" I get the same thing.

I'm trying rssh out to see if this will solve the problem.  At least until they have some sort of default "umask" setting for OpenSSH via sftp.

---

### Post by joech on 2009-06-08
Hi,

This is a great tutorial!

I was able to set up sftp in a chrooted jail on intrepid and was running fine until after (I think) I upgraded to jaunty. Now, when I use WinSCP to access the system, I get the following error:

"Connection has been unexpectedly closed. Server sent command exit status 1.
Cannot initialize SFTP protocol. Is the host running a SFTP server?"

Any help with getting this working again is much appreciated.

Thanks
Joe

---

### Post by joech on 2009-08-03
Never mind! I was able to get it working again. It seems the upgrade process reset the setuid root step. I reran the following step from the tutorial and everything is back to the way it was before! Joy! Hopefully this will help someone else with the same issue.



[COLOR=Blue]In order for the chrooting process to work, "/usr/lib/rssh/rssh_chroot_helper" has to be setuid root. (Note: this path is relative to real root, not chroot root.) To setuid root, run the command:
[/COLOR]  	[COLOR=Blue]Code:[/COLOR]
 	[COLOR=Blue]sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper[/COLOR]

---

### Post by Stan* on 2009-12-25
Many thanks for this howto! One try and it works :) Excellent work.

I've one question though: Can I chroot a user to their own home folder? Because now they can read the whole chroot-folder, above their own home folder.

Thanks in advance. Excellent post.

---

### Post by jchau on 2009-12-26
> **Stan* said:**
> Many thanks for this howto! One try and it works :) Excellent work.

I've one question though: Can I chroot a user to their own home folder? Because now they can read the whole chroot-folder, above their own home folder.

Thanks in advance. Excellent post.

You're welcome.  My answer is no and yes.  

No, you can't hide that stuff in the chroot folder from the user with the rssh setup.  They need to be accessible in order for the setup to work.  That said, the steps in the tutorial removed most, if not all, of the sensitive information from the files in the chroot folder and only kept the stuff necessary for operation.  

But yes, you can create an equivalent setup where only the user's home folder is accessible to the user.  I just updated the main post for this thread with information on how to do this.  (The reason why my original tutorial didn't take this new approach was because this new approach uses features that appeared after I wrote the original tutorial).  

Basically, you use the ChrootDirectory, ForceCommand, Match, and Subsystem keywords in your sshd_config to implement the same chrooted SFTP without a shell access for a user.  

I haven't tried it myself yet (and I probably won't be able to post a new Ubuntu tutorial myself since I'm using Gentoo Linux instead now), but there are many articles about how to do so; here are a few: 
[LIST]
[*][OpenSSH SFTP chroot() with ChrootDirectory]("http://www.debian-administration.org/articles/590") (from debian-administration.org).
[*][Chroot users with OpenSSH: An easier way to confine users to their home directories]("http://blogs.techrepublic.com.com/opensource/?p=229") (techrepublic.com)
[/LIST]

---

### Post by narcisgarcia on 2010-10-10
I've seen this guide for chrooted SFTP, and I've learnt from a lot of tutorials as this. Here my compendium to configure better clients and servers:

[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(special care of users and permissions)

---

### Post by dkerlee on 2010-10-19
I realize that this is years old, but I just got mine working. I was having a problem similar to this one.

My problem was in /etc/rssh.conf

I had uncommented chrootpath = '/home/chroot'

So I recommented that line, and badda bing.

I didn't want to lock this guy into /home/chroot, I wanted him to be able to log into his /home/user dir, but not grant ssh access.




> **juicybananahead said:**
> Hi Jimmy,

Got it working! For your own peace of mind :D, here's the information you were looking for:

First, the verbose output of an sftp attempt.
```
user@ubuntubox:~$ sftp -v -v sft@localhost
Connecting to localhost...
OpenSSH_4.1p1 Debian-7ubuntu4.1, OpenSSL 0.9.7g 11 Apr 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.1p1 Debia n-7ubuntu4.1
debug1: match: OpenSSH_4.1p1 Debian-7ubuntu4.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4.1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-gro up14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-gro up14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour, aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c tr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 137/256
debug2: bits set: 483/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:8
debug2: bits set: 475/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/id_rsa ((nil))
debug2: key: /home/user/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
sft@localhost's password:
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug2: fd 4 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug2: channel 0: request env confirm 0
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 131072
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.3 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 1
Connection closed

```

Second, the syslog entries for the sftp attempt.
```
user@ubuntubox:~$ sudo cat /var/log/syslog | tail -8
Apr 16 23:34:16 localhost rssh[26642]: setting log facility to LOG_USER
Apr 16 23:34:16 localhost rssh[26642]: allowing sftp to all users
Apr 16 23:34:16 localhost rssh[26642]: setting umask to 022
Apr 16 23:34:16 localhost rssh[26642]: chrooting all users to /home/chroot
Apr 16 23:34:16 localhost rssh[26642]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper "/home/chroot" 2 "/home/sft" /usr/lib/sftp-server
Apr 16 23:34:17 localhost rssh_chroot_helper[26642]: new session for sft, UID=1004
Apr 16 23:34:17 localhost rssh_chroot_helper[26642]: could not cd to user's home dir: /home/sft
Apr 16 23:34:17 localhost rssh_chroot_helper[26642]: execv() failed, /usr/lib/sftp-server: No such file or directory

```

Alright, I first noticed that chrooted /home/sft (i.e. /home/chroot/home/sft) could not be cd'd to, so I created a directory like that but I didn't think that would have much of an effect... and right I was. Another failure to sftp. The syslog entries for this attempt:
```
user@ubuntubox:~$ sudo cat /var/log/syslog | tail -7
Apr 16 23:45:29 localhost rssh[26982]: setting log facility to LOG_USER
Apr 16 23:45:29 localhost rssh[26982]: allowing sftp to all users
Apr 16 23:45:29 localhost rssh[26982]: setting umask to 022
Apr 16 23:45:29 localhost rssh[26982]: chrooting all users to /home/chroot
Apr 16 23:45:29 localhost rssh[26982]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper "/home/chroot" 2 "/home/sft" /usr/lib/sftp-server
Apr 16 23:45:29 localhost rssh_chroot_helper[26982]: new session for sft, UID=1004
Apr 16 23:45:29 localhost rssh_chroot_helper[26982]: execv() failed, /usr/lib/sftp-server: No such file or directory
```

Okaaaay... now it's looking for /usr/lib/sftp-server (i.e. /home/chroot/usr/lib/sftp-server). Why is it looking for that? I thought it would be looking for /lib/sftp-server (i.e. /home/chroot/lib/sftp-server). Let's have a look at the entire contents of /home/chroot
```
user@ubuntubox:/home/chroot$ ls -lR
.:
total 20
drwxr-xr-x  2 root root 4096 2006-04-16 07:40 dev
drwxr-xr-x  2 root root 4096 2006-04-16 23:41 etc
drwxr-xr-x  3 root root 4096 2006-04-16 23:41 home
drwxr-xr-x  3 root root 4096 2006-04-16 23:45 lib
drwxr-xr-x  4 root root 4096 2006-04-14 20:44 usr

./dev:
total 0
srw-rw-rw-  1 root root 0 2006-04-16 07:40 log

./etc:
total 76
-rw-r--r--  1 root root 56431 2006-04-14 20:44 ld.so.cache
-rw-r--r--  1 root root    63 2006-04-14 20:44 ld.so.hwcappkgs
-rw-r--r--  1 root root   465 2006-04-14 20:44 nsswitch.conf
-rw-r--r--  1 root root    64 2006-04-16 23:41 passwd
-rw-r--r--  1 root root    76 2006-04-16 23:33 passwd~

./home:
total 4
drwxr-xr-x  2 root root 4096 2006-04-16 23:41 sft

./home/sft:
total 0

./lib:
total 260
-rwxr-xr-x  1 root root 88168 2006-04-14 20:47 ld-linux.so.2
-rw-r--r--  1 root root 26332 2006-04-14 20:49 libnss_compat.so.2
-rw-r--r--  1 root root 34268 2006-03-24 14:34 libnss_files-2.3.5.so
lrwxrwxrwx  1 root root    21 2006-04-14 20:44 libnss_files.so.2 -> libnss_files-2.3.5.so
-rw-r--r--  1 root root 68084 2006-04-14 20:44 libselinux.so.1
-rwxr-xr-x  2 root root 27184 2006-04-14 20:44 sftp-server
drwxr-xr-x  3 root root  4096 2006-04-14 20:44 tls

./lib/tls:
total 4
drwxr-xr-x  3 root root 4096 2006-04-14 20:44 i686

./lib/tls/i686:
total 4
drwxr-xr-x  2 root root 4096 2006-04-14 20:44 cmov

./lib/tls/i686/cmov:
total 1408
-rw-r--r--  1 root root   21864 2006-04-14 20:44 libcrypt.so.1
-rw-r--r--  1 root root 1229936 2006-04-14 20:44 libc.so.6
-rw-r--r--  1 root root    9580 2006-04-14 20:44 libdl.so.2
-rw-r--r--  1 root root   76760 2006-04-14 20:44 libnsl.so.1
-rw-r--r--  1 root root   67364 2006-04-14 20:44 libresolv.so.2
-rw-r--r--  1 root root    9656 2006-04-14 20:44 libutil.so.1

./usr:
total 8
drwxr-xr-x  2 root root 4096 2006-04-14 20:44 bin
drwxr-xr-x  5 root root 4096 2006-04-14 20:44 lib

./usr/bin:
total 56
-rwxr-xr-x  1 root root 18960 2006-04-14 20:44 rssh
-rwxr-xr-x  1 root root 34884 2006-04-14 20:44 scp

./usr/lib:
total 92
drwxr-xr-x  3 root root  4096 2006-04-14 20:44 i686
-rw-r--r--  1 root root 77208 2006-04-14 20:44 libz.so.1
drwxr-xr-x  2 root root  4096 2006-04-14 20:44 openssh
drwxr-xr-x  2 root root  4096 2006-04-14 20:44 rssh

./usr/lib/i686:
total 4
drwxr-xr-x  2 root root 4096 2006-04-14 20:44 cmov

./usr/lib/i686/cmov:
total 1004
-rw-r--r--  1 root root 1022224 2006-04-14 20:44 libcrypto.so.0.9.7

./usr/lib/openssh:
total 28
-rwxr-xr-x  2 root root 27184 2006-04-14 20:44 sftp-server

./usr/lib/rssh:
total 8
-rwsr-xr-x  1 root root 6680 2006-04-14 20:44 rssh_chroot_helper

```

Right, sftp-server is present in /home/chroot/usr/lib/openssh and /home/chroot/lib/. Now, let's make a link in /home/chroot/usr/lib...
```
user@ubuntubox:/home/chroot$ sudo ln /home/chroot/usr/lib/openssh/sftp-server /home/chroot/usr/lib/
```

And try to sftp in...
```
user@ubuntubox:~$ sftp sft@localhost
Connecting to localhost...
sft@localhost's password:
sftp> pwd
Remote working directory: /home/sft
sftp> ls
test.txt
sftp> get test.txt
Fetching /home/sft/test.txt to test.txt
/home/sft/test.txt                            100%    6     0.0KB/s   00:00
sftp> bye
user@ubuntubox:~$ cat ./test.txt
Successful sftp test!

```

Ta-daa! I am honestly not sure what went wrong during setup - was it because my /etc/sshd_config points at /usr/lib/sftp-server as the location of sftp-server?
```
user@ubuntubox:~$ cat /etc/ssh/sshd_config | grep sftp
Subsystem sftp /usr/lib/sftp-server
```

Anyway, I'm just glad to get it working. Thanks for your help, Jimmy!

// Dave

---

### Post by narcisgarcia on 2010-10-20
You can proceed as in my tutorial with OpenSSH, but setting chroot directory to the $HOME in /etc/ssh/sshd_config:

```
ChrootDirectory %h
```

If this is only for 1 user (not for all SFTP-only), you can write a "Match" clause for him:
```
Match User *myname*
```

With OpenSSH server 4.8 or above, you can avoid RSSH patch.

---

### Post by vilwarin on 2011-06-21
I am trying the sftp / rssh approach as described in this tutorial and the 11 pages following it.

I am using LDAP for users, so I think I cannot use the new OpenSSH/chroot-jail approach (linked here: [http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)), because the Match directive only seems to allow local users and groups (and not ldap)

So rssh works without chroot-jail, i.e. if I disable 
```
#chrootpath = "/srv/ftp"
```
everything is working as it should. I can log on to the server with LDAP users, but cannot initiate ssh sessions. (all LDAP users have login-shell /usr/bin/rssh

However I want them restricted to the /srv/ftp directory, so I want it to work with chroot-jail. A sample sftp connection attempt looks like this

```
sftp -v -v harry@localhost
...
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/XXXXX/.ssh/id_rsa
debug1: Trying private key: /home/XXXXX/.ssh/id_dsa
debug1: Trying private key: /home/XXXXX/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
harry@localhost's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to localhost ([::1]:22).
debug2: fd 4 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: subsystem request accepted on channel 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 1736, received 1472 bytes, in 0.2 seconds
Bytes per second: sent 7993.4, received 6777.8
debug1: Exit status 1
Connection closed

```

/var/log/syslog looks like this
```
rssh[13810]: setting log facility to LOG_USER
rssh[13810]: allowing scp to all users
rssh[13810]: allowing sftp to all users
rssh[13810]: setting umask to 022
rssh[13810]: chrooting all users to /srv/ftp
rssh[13810]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
slapd[10203]: connection_read(31): no connection!

```

/var/log/auth
```
sshd[13727]: pam_sm_authenticate: Called
sshd[13727]: pam_sm_authenticate: username = [harry]
sshd[13727]: Accepted password for harry from ::1 port 36959 ssh2
sshd[13727]: pam_unix(sshd:session): session opened for user harry by (uid=0)
sshd[13809]: subsystem request for sftp by user harry
sshd[13809]: Received disconnect from ::1: 11: disconnected by user
sshd[13727]: pam_unix(sshd:session): session closed for user harry
sshd[13727]: pam_winbind(sshd:setcred): request wbcLogoffUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
sshd[13727]: pam_winbind(sshd:setcred): failed to logoff user harry: WBC_ERR_AUTH_ERROR
sshd[13727]: pam_winbind(sshd:setcred): request wbcLogoffUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATrror: PAM_USER_, Error message was: age was: 
sshd[13727]: pam_winbind(sshd:setcred): internal module error (retval = (null)(1398101057), user = 'harry') 
```


I checked all the suggestions here, especially
```
mknod -m 666 /home/chroot/dev/null c 1 3
```
and
```
chmod u+s /usr/lib/rssh/rssh_chroot_helper
```
as these seem to have been the most common mistakes.

I also checked that all libraries listed by ldd `which sftp`
are also located under /srv/ftp/lib
and that all bins listed by
rssh -v
are where they are listed at.

Now I am really out of ideas. Does any of you know what else could be the problem, or what else I could try?

Thanks a lot!

---

