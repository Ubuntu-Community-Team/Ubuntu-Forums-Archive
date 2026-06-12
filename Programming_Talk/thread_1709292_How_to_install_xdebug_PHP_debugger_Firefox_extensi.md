---
title: "How to install xdebug PHP debugger Firefox extension"
date: 2011-03-18
forum: Programming Talk
---

### Post by spoolboyy on 2011-03-18
Hey guys,

Ever wanted to be able to step-through your PHP code?  Me too.  I had heard that a tool called xdebug could help me with this using netbeans.  While looking to install xdebug tonight, I couldn't find a simple, clear tutorial on how to get it done.

Using a firefox extension proved to be the fastest, quickest way to get it going.  Here's how I did it:


Step 1:  Go to this page and install the Firefox plugin:
> [https://addons.mozilla.org/en-US/firefox/addon/easy-xdebug/](https://addons.mozilla.org/en-US/firefox/addon/easy-xdebug/)


Step 1.5:  Restart Firefox.


Step 2:  Install xdebug and setup your php.ini file.  (I'm not 100% sure this step is required, but I did it while following another tutorial / hunch and I'm pretty sure its required.)

>  sudo apt-get install php5-xdebug 

then navigate to:

>  /etc/php5/conf.d 

open up the xdebug.ini file and copy the only line in there.  For me it was this, but it could have changed between now and when you are reading this.

>  zend_extension=/usr/lib/php5/20090626+lfs/xdebug.so 

open up your php.ini file as a user that has write permissions.  Its located here:

>  /etc/php5/apache2/php.ini 

paste the line you copied from the xdebug.ini along with the following four lines into your php.ini file:

> 
xdebug.remote_enable=On;
xdebug.remote_host="localhost;"
xdebug.remote_port=9000;
xdebug.remote_handler="dbgp";


I don't know what those lines do, but both the plug-in author and netbeans claim that I need them.


Step 3:

Open up netbeans and right-click your project.  Select properties > Run configuration > Advanced > and select 'Do not open webbrowser.'


Step 04:

restart apache:
>  sudo /etc/init.d/apache2 restart 


------------USING XDEBUG---------

Step 1:

In netbeans, go to the Debug menu and select 'Debug my project'

Step 2:
Open a browser and point it at your webpage.  In the lower left will be two green icons.  Right click on the 'bug shaped' one and then begin to navigate your page.  

Your code will appear in Netbeans and you'll be able to step through each line, seeing how things go.

Good luck!



Epilogue-----

Hopefully this will help someone save a couple hours of valuable development time.  If I have any errors etc above, let me know.  I don't normally post tutorials but thought this one was simple and would help out somebody in need.

My system info for the information of those trying to recreate this process:

xubuntu 10.04 LTS (32-bit os)
Netbeans 6.8
Firefox 3.6.15
easyXdebug 1.4 (the plugin)

2.2ghz 64-bit CPU
1gb DDR400 ram
200gb hdd
ATI Radeon x200 graphics (yuck)

---

