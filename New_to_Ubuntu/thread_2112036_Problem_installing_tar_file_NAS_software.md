---
title: "Problem installing tar file NAS software"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by raj727 on 2013-02-03
I recently purchased a Synology DS212j NAS device for my home network.  I installed the SynologyAssistant software initially using a Windows 7 pc.  I was able to run the software using a browser similar to setting up a router.  The setup worked well and I was also able to access files on the device using Ubuntu 12.10 by finding files on the device on my home network.

What I couldn't do in Ubuntu was run any Synology software.  I have now attempted to install the Synology Assistant software (Linux version) on my Ubuntu pc.  The installation involved a tar file.  The included instructions are noted below:

   (a) Unpack file "SynologyAssistant-4.1-2647.tar.gz" to the directory
        you want, such as "/usr/local" or ".":

	tar -C ./ -zxvf SynologyAssistant-4.1-2647.tar.gz

   (b) Install the 32bit libraries if you use 64bit Ubuntu:

    	sudo apt-get install ia32-libs

   (c) Create the shortcut to /usr/local/bin:

    	sudo ln -sf /path/install/SynologyAssistant/SynologyAssistant \
	/usr/local/bin/SynologyAssistant

I carried out the following steps to install the software:

- downloaded the zip file from Synology to my download directory, “.../Home/Downloads”.
- unzipped the file in the same directory to get: “SynologyAssistant-4.41-2647.tar.gz”.
- I think I ran the command in (a) above using terminal.  This command was done after I changed to the .../Home/Downloads directory (I think).
- I ran the command in (b) above.
- I followed (c) above as well (I think).

In the end, I ended up with a Synology Assistant folder in the .../Home/Downloads directory which contains six additional folders titled: dcraw, ffmpeg, help, imageformats, imageMagick, and lib.  The folder also contained three files titled: dcraw_LNX.sh , SynologyAssistant and SynologyAssistant.bin

I also ended up with a file in my /usr/local/bin folder titled “SynologyAssistant”.

I'm still uncomfortable with using terminal because I forget to move to move to the directory in which I should run the commands.

Could anyone help with the next steps?

---

### Post by tgalati4 on 2013-02-03
Any executable files need to be marked as executable:

```
which SynologyAssistant
cd /usr/local/bin
ls -la Syn*
sudo chmod +x SynologyAssistant
./SynologyAssistant

```

The *which* command shows you where you installed it or if there are multiple copies.
Assuming it is in /usr/local/bin, then check the permissions of the file using *ls -la*.
If the color of SynologyAssistant is not green--meaning not executable, then you must turn it green.  Green is good, that means it is executable.  To turn it green you must run the *sudo chmod +x* command to add executable privilege to it.

To run it, you use the *./SynologyAssistant* command, that means run the executable from the current directory.  Both the chmod and ./ notation are security measures which limit executables from automatically running.  Unlike Windows, which runs everything whenever it wants, including viruses.

---

### Post by raj727 on 2013-02-03
OK.  I've edited my follow-up based on your detailed response.

Thank you.  I now understand your response.  When I go to start the application, using the "./SynologyAssistant" command, I get an "argument missing" warning with several additional warning messages including I should make sure there is no antivirus applications running.

I do have antivirus software running on my NAS device.  Should I disable this software using a Windows 7 pc and then try running the command again?

---

### Post by tgalati4 on 2013-02-03
You only run ./SynologyAssistant from the /usr/local/bin directory.  From any other directory, you just use SynologyAssistant.  This assumes that /usr/local/bin is in your $PATH.  You can check your $PATH by running *env*--environment or *$PATH*.

```
env
$PATH
```

If you are still missing arguments, then perhaps:

```
SynologyAssistant --help
SynologyAssistant -?
SynologyAssistant -h

```

I don't know if a firewall would affect operation or not.  I don't have a Synology NAS to test with.

---

