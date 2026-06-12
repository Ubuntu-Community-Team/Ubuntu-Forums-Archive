---
title: "HOWTO: Share folders between OS X and virtualized Ubuntu with Parallels and sshfs"
date: 2006-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by davidsiegel on 2006-12-26
I run Ubuntu 6.10 on my MacBook Pro using Parallels because sound and wifi are not supported on a native Edgy installation. Parallels has a "Shared Folder" feature that only works with a Windows XP client. Here is how I do folder sharing between OS X and Ubuntu, but it should work for any Linux or UNIX:

[LIST=1]
[*]In Mac OS X, before starting Parallels, go into the Sharing System Preference's pane and enable Remote Login by checking the box next to "Remote Login."

[*]In Parallels, go into Networking in your client preferences and enable Shared Networking.

[*]Start your Ubuntu client machine and login.

[*]Once in Ubuntu, install sshfs. sshfs is a filesystem built on top of ssh. Run the following in a Terminal (Applications > Accessories > Terminal):

```

% sudo apt-get install sshfs

```

[*]The sshfs install created a new user group called 'fuse'. If your Ubuntu username is 'joe', do the following to add joe to the fuse user group:

```

% sudo adduser joe fuse

```

[*]Log out of Ubuntu then log back in for these changes to take affect.

[*]Now we need to create a password-less ssh key so you can connect to your Mac OS X host via ssh without having to enter a password:

```

% sshkeygen

```

When prompted for a password, just press return to leave the password blank.

[*]The IP address of your Mac OS X host on the shared network should be 10.37.129.2. If that host is unreachable in these next few steps, go to a terminal in Mac OS X and type 'ifconfig' and look for a similar IP address towards the bottom of the ifconfig output - near words like 'share' and 'bridge'. In my experience this address has remained constant.

```

% scp ~/.ssh/identity.pub *osxusername*@10.37.129.2:
*<Enter your OS X user's password when prompted>*
% ssh *osxusername*@10.37.129.2
*<Enter your OS X user's password when prompted>*
*<You should now be logged into an OS X terminal via ssh>*
% mkdir .ssh
% cat identity.pub >> .ssh/authorized_keys
% rm identity.pub
% exit

```

[*]Now we're ready to mount a shared folder. From a Ubuntu terminal, in your home directory (~):

```

% mkdir Documents_OSX
% sshfs 10.37.129.2:Documents Documents_OSX

```

And that should do it. Look inside Documents_OSX - it should have the same contents as your OS X Documents folder.

[*]If you would like to unmount your shared folder, you can either just log out of Ubuntu or do:

```

% fusermount -u Documents_OSX

```

[*](Optional) I created this quick-and-dirty Python script that I saved as ~/bin/mount_sshfs (with executable permissions) and added to my session startup items (System > Preferences > Sessions > Startup programs tab):

```

#!/usr/bin/python

import os
import sys
import getopt

host = '10.37.129.2'

mount_points = [('/Users/dave/Music', '/home/dave/Music'),
        ('/Users/dave/Documents', '/home/dave/Documents'),
        ('/Users/dave/Pictures', '/home/dave/Pictures')]

def main(argv=None):
    if argv is None:
        argv = sys.argv
    try:
        opts, args = getopt.getopt(argv[1:], 'u', ['unmount'])
    except getopt.error, msg:
        print msg
        print 'for help use --help'
        sys.exit(2)
    mount_op = mount
    for option, a in opts:
        if option in ('-u', '--unmount'):
            mount_op = unmount
    mount_op()    
    return 0

def mount():
    argv = ['/usr/bin/sshfs', None, None]
    for mount in mount_points:
        argv[1] = '%s:%s' % (host, mount[0])
        argv[2] = mount[1]
        cmd = ' '.join(argv)
        print cmd
        os.system(cmd)

def unmount():
    argv = ['/usr/bin/fusermount', '-u', None]
    for mount in mount_points:
        argv[2] = mount[1]
        cmd = ' '.join(argv)
        print cmd
        os.system(cmd)

if __name__ == '__main__':
    sys.exit(main())


```

I save this as ~/bin/mount_sshfs and change its permissions to be executable. Whenever I login to Ubuntu, my OS X folder /Users/dave/Music is available in Ubuntu as /home/dave/Music.

[/LIST]

---

### Post by patrik_runeberg on 2011-01-13
Thanks a lot for this great description! I needed to change only the following to make it work immediately:
- The autorization file is named ~/.ssh/id_rsa.pub (not identity.pub)
- When sharing the Documents folder with sshfs the command is:
  sshfs osxusername@10.37.129.2:Documents Documents_OSX

The Python script is perfect when changing:
   host =  'osxusername@10.37.129.2'
   mount_points = ['/Users/osxusername/Documents', 'home/username/Documents_OSX']

/Patrik

---

