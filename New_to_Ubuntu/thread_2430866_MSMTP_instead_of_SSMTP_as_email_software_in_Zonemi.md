---
title: "MSMTP instead of SSMTP as email software in Zoneminder  on Ubuntu"
date: 2019-11-08
forum: New to Ubuntu
---

### Post by bkjaya1952 on 2019-11-08
The [ software MSMTP]("https://marlam.de/msmtp/")  is a latest  SMTP client runs on a wide variety of platforms. It seems  msmtp is overtaking ssmtp which is a software of similar nature.
 At present the Zoneminder has been  programmed  to use ssmtp as an email software under NEW_MAIL_MODULES.
 To send email alerts in zmfilter.pl , a programme has been written to use MIME::Lite module  which uses “sendmail” command.
 The worked example in this blog post shows how to use MSMTP  insted  of SSMPT  in Zoneminder to send email alerts of motion detection events.
  
 **First you will have to install MSMTP ** ( If  ssmtp , sendmail  available , please uninstall completely )
 Open the Ubuntu terminal and run
 sudo apt install msmtp
 After installing , you can find the main executable file msmtp at /usr/bin
[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-21-11-17-51.png?w=700[/IMG]

[CENTER]Figure:- 1 msmtp file created at /usr/bin/[/CENTER]
 **Then create   sendmail file which a symlink of  msmtp ( at /usr/bin)  in /usr/sbin/ .**
 Run on the Ubuntu terminal
 sudo ln -s /usr/bin/msmtp /usr/sbin/sendmail
 Note: before making above symlink , make sure that there is no sendmail file in /usr/bin
 When zmfilter.pl searchs  for /usr/sbin/sendmail , it redirect to msmtp which is the main executable file at /usr/bin/.
[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-20-22-51-42.png?w=700[/IMG]

[CENTER]Figure:-2 sendmail file at /usr/sbin
[/CENTER]
 **Now you will have to create a configuration file called  msmtprc which contains email hosts ,ports ,certificates ,email details  etc at the directory /etc/**
 Creating a ~/.msmtprc file in home directory is not essential as we  are making a file at /etc/ . Then msmtp   by default , connects with     msmtprc at /etc/
 On the Ubuntu terminal
 sudo gedit /etc/msmtprc


[CENTER]
[/CENTER]
 When the empty file is opened, enter the following scripts
 # Set default values for all following accounts.
defaults
auth on
tls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
logfile ~/.msmtp.log
 # Gmail
account gmail
host smtp.gmail.com
port 587
from your gmail address
user your gmail address
password your gmail password
 # Set a default account
account default : gmail

[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-21-22-16-22.png?w=700[/IMG]

[CENTER]Figure:-3 Scripts in /etc/msmtprc
[/CENTER]
 **To add group www-data to the file**
 Then on the Ubuntu terminal
 sudo chown root:www-data /etc/msmtprc
 Now you can try a test mail on the terminal
 echo “Subject: sendmail test” | sendmail -v [EMAIL="bkjaya1952@aol.com"]bkjaya1952@aol.com[/EMAIL]
 Note : replace [EMAIL="bkjaya1952@aol.com"]bkjaya1952@aol.com[/EMAIL] with your receiving email
 **How to make changes in Zoneminder for MSMTP**
 It is assumed that the Zoneminder software is already installed in your Ubuntu PC
 Please refer the following link for installation guide for Zoneminder
 [HOW TO INSTALL ZONEMINDER, v1.33.0. ON UBUNTU 18.10 /19.04]("https://bkjaya.wordpress.com/2018/12/15/how-to-install-zoneminder-v1-33-0-on-ubuntu-18-10-lts-cosmic/")



[CENTER]
[/CENTER]
 Go to Options/Email on the ZM-Console
 And  tick boxes and make changes in the cages as sown in following two figures
[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-21-22-43-28.png?w=700[/IMG]

[CENTER]Figure:-4Upper part of the page at Options/Email
[/CENTER]
 **Please note the following additional entries under EMAIL_BODY cage**
 Attach (first) event image with the highest score : %EIM%
 Attach event mpeg video : %EV%
[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-21-11-10-46.png?w=700[/IMG]

[CENTER]Figure:-5 Lower part of the page at Options/Email
[/CENTER]
 **Making a filter to initiate email process**
 Make a filter as shown in the figure below and execute
[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-21-09-47-52.png?w=700[/IMG]
Figure:6 filter to select events of maximum score is > or= to 5 and send email alerts


[CENTER]

[/CENTER]
 Following 2 figures show the received emails
[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-21-11-11-31.png?w=700[/IMG]

Figure:- 7 received email alerts
[IMG]https://bkjaya.files.wordpress.com/2019/10/screenshot-from-2019-10-21-12-44-34.png?w=700[/IMG]
Figure:- 8 received email alerts

---

