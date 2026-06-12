---
title: "Update and install gnu radio"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by jems.pradhan on 2013-10-27
I am a new user of Ubuntu and I have installed Ubuntu 12.04 in my Pc. I have been facing a lot of problems.

Problem 1 : I have not been able to update. I enter the command  "sudo apt get-update" in the terminal and it starts updating and gets stuck showing " 0% [Connecting to archive.ubuntu.com (2001:67c:1360:8c01::19)] [Connecting to security.ubuntu.com (2001:67c:1562::15)]

Problem 2 : I have been trying to install GNURADIO software in my 32 bit windows pc but I have not found a full resource to install the gnuradio software. It would be great if I could get the full instruction to install this software and use my USRP device. 
                  After looking the website of ubuntu I came across several methods and first I tried to install the pre-requisite Raring Ringtail (13.04). I copied the commands given on the website is showed the error 

                                                         "E: Unable to locate package libboost1.53-all-dev
                                                          E: Couldn't find any package by regex 'libboost1.53-all-dev'
                                                          E: Unable to locate package sdcc
                                                          E: Package 'python-wxgtk2.8' has no installation candidate
                                                          E: Package 'python-qwt5-qt4' has no installation candidate
                                                          E: Package 'libqwt5-qt4-dev' has no installation candidate"

I have also tried to update from the update manager but it gets stuck in applying changes.

I would be very happy if I could get urgent support in installing GNU RADIO and work with my USRP device.

Thanks,

---

### Post by jems.pradhan on 2013-11-14
Firstly, before installing a GNU Radio software in a Linux Operating System one must be aware of the space in the drive where the Linux Operating System in installed.

After installing the Ubuntu 12.04 in my laptop I tried to install the GNU Radio on my Laptop. Since, I had only 2 GB of space left in C Drive where the Ubuntu 12.04 was installed my laptop got hanged every time I tried to install GNU Radio software. So, firstly I managed a lot of space in my C drive around 40 GB by deleting the windows.old folder ( the folder of my old operating system).

The steps to successfully install the Ubuntu 12.04 in Windows Platform and GNU Radio are as follows:

**Step 1**: Installing Ubuntu 12.04 is very simple. It is like downloading and installing an application. There are many methods of running an Ubuntu platform and I found this one to be the easiest. Firstly go to the official page of Ubuntu or you can directly go to this link.

[http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

This link might change with time and updates.

**Step 2**: Type Windows Installer in the search box.

**Step 3**: Click on **Installing Ubuntu with windows installer | Ubuntu1**

**Step 4**: Click on **Windows Installer**

**Step 5**:Click on **Get the Installer**

**Step 6**: Go to the bottom of the page and click on **Not now, take me to the download**

**Step 7**: Once you click this the **Wubi.exe** will start downloading. It might take some time depending on        the speed of the internet. Once you download this exe file you are ready to install Ubuntu. It might take some time for installing depending upon the configuration of the computer.  (You will have to type in the username and password for running the ubuntu.)

After successfully installing and restarting the computer you are ready to run the Ubuntu.

There are many methods to The steps to install the GNU Radio software after installing the Ubuntu are as follows:

**Step 1**: Open the terminal by pressing **Ctrl+Alt+Tab**

**Step 2**: Type the following command on the terminal **sudo apt-get update**

Update can take some time and one has to be very patient. It took a very long time for me to update in my research lab desktop which is a high end device compared to my laptop which is comparatively very low end device and probably because it was in my school network. So, once you type this command you will have to be very patient until all the updates have been completed.

**Step 3**: Once all the updates have been done type the following command in the terminal.

**wget [http://www.sbrac.org/files/build-gnuradio](http://www.sbrac.org/files/build-gnuradio) && chmod a+x ./build-gnuradio && ./build-gnuradio**




This command will download and install all the dependencies, download and installs both the UHD and GNU radio. This can take a very long time so one has to be very patient. It can take more than an hour. One should not panic if the screen stays stable for a very long time.

---

### Post by newb85 on 2013-11-14
I'm glad you were able to solve your problem, and it's good that you posted the solution.  But there are a few things that should be said.

First, the Windows installer is not a recommended installation method for Ubuntu.  Canonical used to push its use, but it has had too many problems.
Second, it's probably not a good idea for people to install 13.04 anymore, as it will hit EOL in two months.  Best to install 12.04 LTS or 13.10 at this point.
Third, gnuradio is already in the Ubuntu repositories.  One has but to install it using either the Software Center or apt-get, and dependencies are handled automatically (including the UHD libraries).  Compilation shouldn't be necessary, unless for some reason you need the absolute latest (and unstable) version.

---

### Post by jemspradhan702 on 2013-12-02
Thank you very much. If Windows Installer is not the perfect method the you could post the step by step perfect method for Ubuntu and Gnuradio installation because it is really a problem for a new user like me.

---

### Post by newb85 on 2013-12-02
The best method is to create bootable media (either DVD or USB).  If you go to [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support), along the right side are links according to what OS you're creating the media from and which media you want to use.  (The Windows Installer is also listed there, unfortunately.  Disregard it.)

Once you've created the DVD/USB, boot your machine from it.  If you select "Install Ubuntu", you will be taken through an installation wizard that will install Ubuntu on its own partition alongside Windows (assuming you don't elect to overwrite your Windows system).

Once you've installed Ubuntu and rebooted, you can easily install gnuradio from the Software Center.

---

