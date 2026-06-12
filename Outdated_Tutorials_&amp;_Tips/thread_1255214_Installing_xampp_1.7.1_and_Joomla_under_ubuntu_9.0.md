---
title: "Installing xampp 1.7.1 and Joomla under ubuntu 9.04 Linux"
date: 2009-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by johnocon999 on 2009-09-01
[SIZE=4]**Installing xampp 1.7.1 and Joomla under ubuntu 9.04 Linux.**[/SIZE] (by johnocon999)


[SIZE=3]**Installing xampp**[/SIZE]
-----------------
1: Download xampp 1.7.1 for Linux to your desktop. **[SIZE=4]NB: IT MUST BE XAMPP 1.7.1[/SIZE]**  Download from here - [http://sourceforge.net/projects/xampp/files/XAMPP Linux/]("http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/")

2: Extract to /opt folder in your **system files area**. The best method of doing this is to do it through the console. You seem to get more permission problems when you dont do it through the console. (I tried it a thousand times from the desktop without complete success. It will extract but will not run without errors).

Use the following command - **sudo tar xvfz xamp-linux-1.7.1.tar.gz -C /opt**

3: To start the server do the following in your console.  **sudo /opt/lampp/lampp start**

4: All services should start.  
-To stop the server running **sudo /opt/lampp/lampp stop**  
-or to restart if its already running **sudo /opt/lampp/lampp restart**

5: To check your installation open browser window and type **[http://localhost]("http://localhost/")** (If the installation was successful you should see xampp main page. Choose your language. Check to see all is working correctly. Check to see that you can enter the myphpadmin section of xampp and create a database without any errors. Hopefully success!


**[SIZE=3]Installing vsftpd (ftp server)[/SIZE]**
------------------
I know ftphd comes with xampp. But I found it easier to configure vsftpd (as I am a novice)
1: Open System > Administrator > Symantic packet manager and search for and install vsftphd
2: To configure vsftpd open the following file **/etc/vsftpd.conf** to change the default settings.

---------------------------------------------------------------------------------------------------------------------
When you open the file just remove the hash symbol from infront of the following commands
**#Local_enable=yes**  (by uncommenting this you will be able to log into ftp using your linux username and password)
**#write_enable=yes**  (will allow you to download and upload files)
---------------------------------------------------------------------------------------------------------------------

The configuration file consists of many configuration parameters. The information about each parameter is available in the configuration file. Alternatively, you can refer to the man page, man 5 vsftpd.conf for details of each parameter.

To run the vsftpd daemon use the following command:

 **sudo /etc/init.d/vsftpd start **

Hopefully success.


**[SIZE=3]Installing Joomla[/SIZE]**
-----------------

1: Download latest version of Joomla from joomla.org

2: The Joomla archive you just downloaded will have to be extracted to the** /opt/lampp/htdocs/** folder. Open up console window and type **sudo nautilus**. Now go to the **opt/lampp/lampp/htdocs** and Create a folder called **myjoomlasite**. Right click on folder and set permissions **OWNER ROOT CREATE AND DELETE FILES, GROUP ROOT CREATE AND DELETE FILES Allowing executing - NO**. If you are not able to extract to this folder after changing the permissions. Open the sharing tab and SHARE the folder. You should now be able to extract the archives contents to Myjoomlasite.

3: To see if your installation was successful so far, open browser window and type **[http://localhost/myjoomlasite](http://localhost/myjoomlasite)** and press return. Hopefully you will be brought to the index.php page and be able to start setting up your joomla site. NB: Make sure no sql errors are displayed at the top of the page.

4: Before proceeding anymore open your xampp server **[http://localhost/xampp](http://localhost/xampp)**, click on **myphpadmin **and create a mysql database to use with your site. setup a user name for the database under the privileges section and grant all privileges click go. Your database should now be setup.

5: Go back to your joomla setup and continue with the following steps

-** select language** >next
-** pre installation **check (this checks if all the minimum system requirements are met) >next
-** Licence** >next
- **Database** (enter database details)
      Database type: MYSQL 
    Host:Localhost 
    Database Username:
    Password:
    Database Name: (what u called your joomla database)
        >next.
-** FTP LAYER** has to be setup if you wish to add components to joomla under linux. We have already setup vsftpd so this should be a breeze. You will be required to enter a USERNAME,PASSWORD AND FTP PATH. Username is your linux username:**** password:sad:is your linux username password) In order to get the ftp path click Auto find path. Hopefully your path will have being found eg /myjoomlasite
>next

- **CONFIGURATION **   - by default the username is admin.  And the password is the password you set. The rest is self explanatory
>next

- Before you do anything else you must remove the installation directory from your myjoomlasite folder. Go to **/opt/lampp/lampp/htdocs/myjoomlasite **and delete the installation directory.

*you should now be able to login into your sites administrator section.*  To view your site go to **[http://localhost/myjoomlasite](http://localhost/myjoomlasite)**

Hope this tutorial has being of use.   I was hours trying to work this out as Im new to Linux (only a week). And I love it!

---

### Post by asith on 2009-11-05
[***i am very new to ubuntu ***]("http://www.google.lk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=3ow&ei=RHjySuHPEY6i_AbN48CoAw&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=joomla+error+after+installation+on+ubuntu+9.04+No+configuration+file+found+and+no+installation+code+available.+Exiting...&spell=1")
[***error arised after instalatin directary deleted as "*** No configuration file found and no installation code available. Exiting..."]("http://www.google.lk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=3ow&ei=RHjySuHPEY6i_AbN48CoAw&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=joomla+error+after+installation+on+ubuntu+9.04+No+configuration+file+found+and+no+installation+code+available.+Exiting...&spell=1")
what to do next
:KS

---

### Post by johnocon999 on 2009-11-07
Hi,
Are you sure you deleted the correct directory. 
Do not delete the Myjoomlasite directory.  Its the installation directory within this directory that you delete.

Just checking.
Let me know

---

### Post by darksideforge on 2009-11-10
Jon,
As you seem to be knowledgeable, let me ask a quick question please (yes, a teensy bit of a hijack but I don't see another thread in my search that looks like it would help).

If I have a website ready to be launched, and that website is xhtml/css with drop down menus and background colors and pictures etc etc, am I going to have to re-do the entire thing in order to have my site hosted on a Joomla server, or is there a viable alternative?  There's more to this story but I'll save it unless you want to hear it.

Well, on second thought, let me expound a bit.

A friend of mine has a website. She is very unhappy with it. It is hosted by a hosting company that does design work as well as hosting.  She asked me if I would design her a new website. I pulled up Bluefish and started creating and doing and redoing until she was happy.  She LOVES the way the new site looks.

Now, how do I upload the website to the Joomla-based hosting company?

I've logged in using my friend's login/password info to (ex) [http://www.friendssite.com/administrator](http://www.friendssite.com/administrator) and I'm now faced with numerous options. I googled my question and I found two sites with titles like "5 Steps To Easy Joomla Migration" etc etc etc.  But what I'm seeing is that they want me to recreate my menus, recreate background colors using some sort of WYSIWYG editor that's built-in, and generally cut/paste all of the text from my website over into some forms.

What I want to be able to do is load my file directly to their server, a la:
```
/var/www/vhosts/myfriendssite/NEWSITE
```
and yes, the Joomla hosting company is using Apache/Linux.

Or, am I going to have to call the hosting company and tell them that their services are no longer required and that we'll be moving the domain elsewhere?

Thanks in advance.

---

### Post by johnocon999 on 2010-02-22
Hi and sorry for the extremely late reply.  Have not being here since November.  To answer your question about the site you developed using css and xhtml.  There are numerous tutorials on the web which will guide you through the process on how to develop such templates. In order for the site your working on to work as a Joomla site you must develop it as a Joomla template.   I design professional templates for Joomla. You can check them out at [http://www.joomlage.com](http://www.joomlage.com).    I have a tutorials section on my site which you can use to help you install your Joomla template once you have it developed.  All the Best. John.  Anymore questions feel free to ask. Just fill in the contacts form on [http://www.joomlage.com](http://www.joomlage.com) or email me at [email]info@joomlage.com[/email]

---

### Post by Chris_Nik on 2010-04-01
Hello,
i get this message ''No configuration file found and no installation code available. Exiting...''

Can you help me...

---

### Post by walt11 on 2010-06-30
> **johnocon999 said:**
> [SIZE=4]**Installing xampp 1.7.1 and Joomla under ubuntu 9.04 Linux.**[/SIZE] (by johnocon999)


[SIZE=3]**Installing xampp**[/SIZE]
-----------------
1: Download xampp 1.7.1 for Linux to your desktop. **[SIZE=4]NB: IT MUST BE XAMPP 1.7.1[/SIZE]**  Download from here - [http://sourceforge.net/projects/xampp/files/XAMPP Linux/]("http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/")

Thanks for your very good instructions, which have been extremely helpful. I already had XAMPP 1.7.3a installed, and tried to install Joomla under that,  but got a fatal error (described below) at the very end of the Joomla installation process, and am wondering if it could be due to the different version of XAMPP. You're very explicit about using 1.7.1. Is it just because that was the latest one when you did this, or is there something about that release which Joomla needs to have? Another difference I have from you is that I'm using ubuntu 10.04.

Having said that, here's the error. After clicking "Next" at the end of the Joomla installation, I received these 2 messages:
```
Notice: Undefined index DBtype in /opt/lampp/htdocs/joomlasite/installation/installer/models/model.php on line 764

Fatal error: Call to undefined method jException::getNullDate() in /opt/lampp/htdocs/joomlasite/installation/installer/helper.php on line 290

```At several other points in the installation, I got this (non-fatal) error:
```
Error: the XML response that was returned from the server is invalid

```That kept me from loading the examples, or verifying the FTP configuration.

(Another difference from your installation is that I used the proftpd that came with XAMPP rather than vsftpd, but doubt that could have caused these problems.)

Thanks for any help you can give.

ADDED 07/01/10:
I was able to install Joomla manually (described in detail at  [http://help.joomla.org/content/view/1944/302/](http://help.joomla.org/content/view/1944/302/)). The web install that you described is much to be preferred, but I couldn't get past the error. The manual way of doing it is much longer and more detailed, but it gives you more control of the process. There were some problems, and I had to edit the php.ini file, but it's working.

---

### Post by ozstar on 2010-07-03
This link in the top of this thread is WRONG!

Use the following command - [B]sudo tar xvfz xamp-linux-1.7.1.tar.gz -C  /opt

You need the two pp's in xampp!!

Took me ages of errors to find it.

Hope it'll save you..

I also used 1.7.3a

Good Luck!
[/B]

---

### Post by walt11 on 2010-07-03
> **ozstar said:**
> This link in the top of this thread is WRONG!

Use the following command - **sudo tar xvfz xamp-linux-1.7.1.tar.gz -C  /opt**

Thanks for the info. I had already installed XAMPP when I found this thread, but was running into problems installing Joomla on top of it ( my post #7 above). Couldn't get the easier web install for Joomla to work for me, so used the manual method. That worked (with some difficulty), and I now have Joomla installed and running, although I've encountered some permission problems. When I try to make changes from the administrator page which would modify configuration.php, I get an error message telling me I can't open the file for writing, and I've had to edit it manually. Have been trying to modify permissions, but so far, that hasn't helped.

---

