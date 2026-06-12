---
title: "subversion"
date: 2007-04-14
forum: Programming Talk
---

### Post by Menyus on 2007-04-14
Hello All,

I am a newbe and I'm trying to setup accessing the subversion (v 1.3.2) repository on my Ubuntu 6.10 server from my XP workstation and I am having no luck at all. I have read though HOW-TOs for svn+ssh and SSH key authentication and have the book “Pragmatic Version Control using Subversion”, 2nd ed. Unfortunately, none of these have enough details for a newbe like me on how to set this up.

My goal is to be able to access the svn repository either from within ecplise on the xp maxhine using the sublcipse svn plugin or from Windows Explorer using TortoiseSVN.

I have verified the subversion installation on the server and it seems to be working fine. Also, svnserve is running as a daemon. I have added the line to the subversion config file in the [tunnels] section 

ssh = C:\Program Files\PuTTY\plink.exe

I also experimented with TortoiseSVN and SSH-2 RSA keys generated with puttygen.exe to no avail. 

For example, when I try to add a new repository in eclipse (URL: svn+ssh://ubuntu-server/sesame/trunk), I get the following error message:

The system cannot find the file specified.  
svn: Can't create tunnel: The system cannot find the file specified. 

In Windows, I tried the command line with the following results:

D:\dev>svn svn://ubuntu-server/sesame/trunk sesame
'svn' is not recognized as an internal or external command,
operable program or batch file.

I also installed TortoiseSVN but when I right click in Windows Explorer and select SVN checkout, I get

Error: URL 'svn://ubuntu-server/home/cnemeth/svn-repos/trunk' doesn't exist  

Does anyone know about detailed instructions on how to do this? Please help! I have wasted much too much time on this. I just want to get some work done.

Thanks,

---

### Post by rmemm on 2007-04-14
You should install svn and Tortoise on your windows system.  SVN will give you the svn command but you'll use Tortoise most.  You can use svn+ssh I think -- but I would in general  recommend the apache setup -- though it may be more work for you -- meaning https -- and that's what I use myself.

I'm not certain why you can't find the repository -- but I suspect that you need the full path from the linux root directory after the server.  I think I seem to remember that your user account will need write access to the svn files also -- check the documentation on this.  Security is one down side of the svn+ssh setup I seem to remember.

My point is -- the first thing I would do is check file access permissions and that you have all of your files setup -- and you've created the repository and that in the repository exisists.  You can do this all with local svn commands on the linux system.

Also -- make certain ssh is setup and works as you excpet just by connecting from your windows system. You can use cygwin or putty to test this.

Rob

---

### Post by Menyus on 2007-04-15
mem,

Thanks for the pointers. I should mention that I have verified locally that subversion is setup and functioning correctly on the server. I was able to create a repository and manipulate the content, i.e.,     import, commit, co,  log, diff, etc. I can also access the server through PuTTY using ssh.

---

### Post by rmemm on 2007-04-15
The main doc for this is "Version Control with Subversion" -- [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/).  I assume you've seen this book, but you didn't mention it.  There is a chapter on what you want to do.

I took a quick look at chapter 6 to refresh my memory a bit -- it's been a couple of years since I've tried this.  Here are some thoughts in no specific order:

*  I would consider getting the vanilla SVN setup going first -- it's easier and make sure you can use that.  Then work on SSH maybe.

*  I'd focus on either svn or Tortoise interface first and get one of those working.  maybe svn because it's the most basic.

*  I noticed in your example you used svn: in tortious.  That won't work in the ssh setup -- you have to use a consistent prefix (like svn+ssh) and a consistent following url in all cases.

*  I would not use putty to do the tunneling -- I not sure -- but I think both svn and Tortoise come with their own ssh client.  So probably best to get rid of anything special from your client side setup.

*  For svn+ssh -- svnserve does not need to be running as deamon.  Instead what happens is svnserver -t is launched over the ssh connection and access is direct file system access just as if you'd been logged into the remote host.  Because of this your user account needs to have rw access to the repository tree.

*  As an aside, if you want to use the daemon mode -- then you have to use non-encrypted connection (ssh:).  You can encrypt this by manually setting up a tunnel with putty from your windows host to your linux box and then reference the svn: server by the port on the local windows machine.  This approach works but it's annoying to use.

*  I would check to see what banners an messages are printed when you just run ssh from the console with things like:  ssh user@myhost or ssh user@myhost ls (where ls is a command).  I've had problems with some programs if the init files print some message -- some programs get confused with the extra text especially in the later case.  Sometimes .bashrc or one of the other init scripts can cause these shorts of issues by printing something.

*  I can't quite remember -- but I don't actually think you need to setup personal keys to use the ssh service.  You can -- but I don't think it's required. I think it's also possible too if they are setup wrong that could be an issue -- or if your have strick host key checking on and the host key is wrong that can cause issues.
 
*  In your 3 examples I think each could have failed for different reasons.  The Eclipse example -- maybe it couldn't find plink.exe.  In the svn example either svn is not installed or the svn.exe command is not in your path -- and in fact the command was invalid even if svn had been installed and in your path.  In each of the examles you used a different path -- do we know all of these are correct.  Generally I'd use the same path and start near the top of the repository.  Also -- you mixed svn and svn+ssh examples -- for svn+ssh and svn: the setups are different totally different on the server side, the user names are different, and the passwords will in general be different.  svn: uses the daemon and a separate user file to configure and authenticate.  svn+ssh uses ssh to authenticate then standard file system access.

*  As I said before -- I think you need to be careful about paths.  For svn+ssh I think you need to use the exact path you used for file system access starting with / and then add svn+ssh://servername to the front of that.  And you might need user@servername not just server name also.

*  Other thing -- if your using the svn: approach -- look at the svnserver.conf file and make sure you have the permissions set properly, have defined users and passwords etc. too.  Also for the deamon to work -- the deamon (not your user account) needs to have rw access to the repository tree.

I don't know if any of this helps -- but it may trigger an idea.

Hope this is of some use.

Rob

---

### Post by Menyus on 2007-04-15
Rob,

First, sorry for misspelling "rmemm". 

Thanks for the pointers. I do have the red book but I have not spent much time reading it yet. I guess now will be the time. 

What I am puzzled about is that sublipse is an svn client that works from within eclipse. As long as my svn server is working and can connect to it, subclips should be able to talk to it. However, it consistently reports not being able to find path. I am happy to report though that I can connect to subversion from my Ubuntu workstation (same machine, dual boot XP/Ubuntu) using the command line (and svnserve). 

Well, I guess it's time to dig in. 

Thanks,
Csaba

---

### Post by rmemm on 2007-04-15
Thing I would say about eclipse is historically it's been a work in progress.  I've played with it but don't use it and haven't looked at it for a few years.  My point though -- getting the basic svn command to work is a good starting point -- because it should work with the least potential issues.  

I've also personally had really good luck with TortoiseSVN as well and that's what I use day to day so I can say that program works pretty well also. Though-- this is with the disclaimer -- I use the apache web setup.

I know there are both Visual Studio and Eclipse plugins -- but I can't say much about the quality of either.

Rob

---

### Post by rmemm on 2007-04-15
Other thought -- could it be a firewall setup?  It would be worth trying to see if you can telent to the svn server port from your windows box -- and as I said before if the svn command uisng svn:// form works.  If this works -- then the basic server is setup and it's something in Eclipse.

And as I said before -- getting svn:// working is a good way to start but it will say nothing about the ability for svn+ssh:// to work.

Rob

---

### Post by Menyus on 2007-04-15
As I mentioned before, my workstation is dual boot: XP/Ubuntu 6.10. 

from XP I can ping the server and can get to it and work with it through a PutTTY terminal (using ssh2). However, the svn:// command does not work. I get an error message saying 

"'svn' is not recognized as an internal or external command, operable program or batch file"

When I boot the same machine into Ubuntu, the svn:// command works (no other changes made). So it must be a Windows setup thing.

---

### Post by rmemm on 2007-04-15
Sorry, I missed that you had booted under windows and linux on same host.  When you were talking linux -- I was reading -- server with Linux and svnserver on it.  Great.  That means something on windows side. 

The svn setup on windows.  Did you install the svn pacakge on windows?  Windows does not come with it, nor does Tortoise.  It is a special install.  Once you install on windows -- track down the svn.exe executable and put that directory in your PATH if it does not do this automatically (I don't know if it does).  You do that with My Computer>Properties>Advanced>Environment Variables or something like that.  There is a PATH variable that is a ; separated list of dirs.  Be careful while editing your path -- it's really bad if you delete it or corrupt it accidently.

Then from any shell you should be able to use that.  Is it possible that Eclipse needs svn.exe and just can't find it?  That makes some sense based on the eclipse message.

Rob

---

### Post by Menyus on 2007-04-19
I finally got around installing subversion on my xp box which solved the problem. For now, I can at least use svn:// in all three places: the command line, TortoiseSVN and eclipse. Thanks for all your help.

---

### Post by chandrala on 2008-04-29
Hello all,
Sorry,I couldn't find the way to post a new thread....So,I have to post my question here.:(
  I have recently started working on subversion,its my 1st time to work on this project(very much a newbie).I have managed to install svn 1.4.5 and Tortoise svnserve 1.4.8 on my pc running on WinXP.I have also managed to create my test repository.I am able to import a test project to populate the repository.Checkout and checkin also work fine as long as,I am accessing the repository locally.
  My problem is as follows:
     
   When I try to access the repository from a remote client     
   machine using TSVN Repo-Browser,I get the following message:

   Unable to open an ra_local session to URL,Unable to open    
   repository.
 While giving the URL name prompted by Tortoise,I have used all combinations of protocols(svn://. . . ./repos name,   file:///..../repos name etc..)However,NOTHING seems to work.Any help on this wil be highly appreciated as I have been struggling to resolve this problem from the past 8 days and my boss threatens to take me off to this project..Please help.. 

Thanks in advance..

Regards,
Chandrala..

---

