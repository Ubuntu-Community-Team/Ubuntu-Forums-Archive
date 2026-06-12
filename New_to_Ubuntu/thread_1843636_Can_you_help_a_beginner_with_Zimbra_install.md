---
title: "Can you help a beginner with Zimbra install"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Graeme-Duncan on 2011-09-13
Hi
I am totally new to Linux. I have successfully installed Ubuntu 64 bit desktop on my Dell 64 bit server (easily achieved) and want to install Zimbra.

I previously had Zimbra working within 30 minutes using Turnkey Linux but it's an old version.

I have downloaded Zimbra to the PC but I am struggling to launch the installer. I am very familiar with Windows server setups and understand all the Mail server stuff (DNS, MX, network settings etc.).

Is there an easy way to launch the install script? Missing that setup.exe option!?!

Sorry for the dumb quiestion but would really appreciate some help.

Kind regards
Graeme

---

### Post by demonipuch on 2011-09-13
Taken from the official Zimbra documentation ([http://www.zimbra.com/docs/ne/latest/single_server_install/](http://www.zimbra.com/docs/ne/latest/single_server_install/)) I urge you to read :
> Open an SSH session to the Zimbra server and follow the steps below.
1.
Log in as root to the Zimbra server and cd to the directory where the Zimbra Collaboration Server archive tar file is saved. Type the following commands:
•
tar xzvf [zcsfullfilename.tgz], to unpack the file.
•
cd [zcsfullfilename] to change to the correct directory.
•
./install.sh to begin the installation.
The install.sh script reviews the installation software to verify that the Zimbra packages are available.

---

### Post by jimbo99 on 2011-09-24
The guy that responded was wrong.  He gave you absolutely nothing to work with.  I'll answer questions if you answer some.

Did you first set your FQHN?  If so, what did you call it?

Do you plan on using it for your mail internally?  If so, how did you set up your split dns?  Do you have sample config files to present?  Did you try to use named only to find there is none when setting up split dns?

Anyway, you have to set the fqhn first.  Then, unless you are an administrator account (which you should not be), then you will need to proceed your commands with sudo.

So, he was right in saying to extract to a folder.  You can right click on the archive and say "extract here" and it will do the same thing he said to do at the command line.  Once done I would recommend you rename the folder to something short.

After you have that, then at the command line, you want to invoke the installer.  The name of it is "install.sh".  Since it isn't marked as an executable you'll have to tell the system to launch it as one.

That's what the "./" is for.

So, at the command line, in the folder where you extracted the files, you would type "sudo ./install.sh".

Answer to proceed and that you agree to the EULA.  Then hope your FQHN is proper.

If so, then just accept the defaults for the rest until you are prompted to set the password for the admin account.

---

