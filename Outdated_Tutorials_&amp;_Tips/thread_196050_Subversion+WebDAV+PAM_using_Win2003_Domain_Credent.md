---
title: "Subversion+WebDAV+PAM using Win2003 Domain Credentials on Ubuntu 6.06 LTS"
date: 2006-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Norton on 2006-06-13
**Installing OpenSSH**
Pop up a terminal, and sudo gedit /etc/apt/sources.list
Remove the cdrom source line

Add "universe multiverse" to the first deb line after "dapper" so that it looks like this:

      deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

save and quit

then run

      sudo apt-get update

      sudo apt-get install openssh-server

You're done.

**Installing Development Tools** - *Optional*

Run these commands.

      sudo apt-get install build-essential

      sudo apt-get install linux-headers-$(uname -r)

      sudo apt-get install monodevelop mono mono-gmcs
[B]
Install FreeNX[/B]
For 32-bit Systems

Run these commands.

      sudo gedit /etc/apt/sources.list

add these lines to the top.

      # FreeNX

      deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx

now run these commands.

      gpg --keyserver subkeys.pgp.net --recv-keys 1135D466

      gpg --export --armor 1135D466 | sudo apt-key add -

      sudo apt-get update

      sudo apt-get install freenx

Use the NoMachine Keys

You're Done.


For AMD64 (might work)

Run these commands.

      sudo gedit /etc/apt/sources.list

add these lines to the top.

      # FreeNX

      deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx

now run these commands.

      gpg --keyserver subkeys.pgp.net --recv-keys 1135D466

      gpg --export --armor 1135D466 | sudo apt-key add -

      sudo apt-get update

      sudo apt-get source nx freenx expect fakeroot cdbs autotools-dev dpatch debhelper patchutils autoconf automake1.4 libjpeg-dev libpng12-dev libssl-dev libx11-dev libxaw7-dev zlib1g-dev

      cd nx-nx-1.4.92+1.5.0/

      fakeroot dpkg-buildpackage -b (Go get coffee, this takes forever)

      sudo dpkg -i ../*.deb

      cd ../freenx-0.4.4+0.4.5

      fakeroot dpkg-buildpackage -b

      dpkg -i ../freenx_0.4.4+0.4.5-4ubuntu2_all.deb

Use the NoMachine Keys

You're Done.

**Installing Apache 2.0 (WebDAV, PHP)**

Run these commands

      sudo apt-get install apache2

      sudo apt-get install php5

**Installing Samba/Winbind** - (pam_mkhomedir, login, ad)

run this command

      sudo apt-get install samba winbind

Now, the first thing we are doing is setting up samba/winbind to work with the domain, so do a nano /etc/samba/smb.conf and insert the following lines:

      workgroup = MYDOMAIN

      idmap uid = 10000-20000

      idmap gid = 10000-20000

      template shell = /bin/bash

      template homedir = /home/%D/%U

      winbind enum users = yes

      winbind enum groups = yes

      winbind cache time = 10

      winbind separator = +

      security = domain

      password server = *

      winbind use default domain = yes

Remeber that this is just and example, you should/can change the values according to your needs.

After that we need to make the system to use winbind.

First edit /etc/nsswitch.conf and

replace:

passwd: compat

group: compat

with

passwd: compat winbind

group: compat winbind

Now go to /etc/pam.d and edit the following files:

common-account:

      #Commented for winbind to work

      #account-required pam_unix.so

      account-required pam_winbind.so

common-auth:

      auth sufficient pam_winbind.so

      auth required pam_unix.so nullok_secure use_first_pass

common-session:

      session required pam_unix.so

      session required pam_mkhomedir.so umask=0022 skel=/etc/skel/

sudo:

      auth sufficient pam_winbind.so

      auth required pam_unix.so use_first_pass

Finally, there are only a few things left to do:

Join the domain:

      net rpc join -D MYDOMAIN -U Administrator

Test it with:

      wbinfo -u

      wbinfo -g

Make the domain home dir (users home dirs will be inside this one, but can be configured in smb.conf):

      mkdir /home/MYDOMAIN

You're Done!

**Installing Subversion**

run this command

      sudo apt-get install subversion libapache2-svn libapache2-mod-auth-pam

      sudo mkdir /usr/local/svn

Edit /etc/apache2/mods-enabled/dav_svn.conf

uncomment DAV and SVNPath

change SVNPath to SVNParentPath and have it point to /usr/local/svn

Before the </Location> tag, paste this

      AuthPAM_Enabled on

      AuthType Basic

      AuthName "Subversion Repository"

      Require valid-user

save/quit

      sudo /etc/init.d/apache2 restart

**Installing WebSVN**

      sudo apt-get install websvn enscript

Our repositories are in /usr/local/svn - please use that.

Yes to all.


----

That's it, you're done.

You're Ubuntu server should now happily co-exist on any NT Domain based network. Congrats.

-Norton

---

### Post by mamanmapillai on 2007-11-29
hai,

I have setup svn by seeing this document.
When I run in browser it asking username and password.
How to create username and password for svn.
And where it stores username and password.
Can u please give me detailed document.so that it will be helpful to setup svn.

Thanks.

---

