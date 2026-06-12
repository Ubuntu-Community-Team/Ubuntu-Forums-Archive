---
title: "Ubuntu 11.10 needs IcedTea Java 6 Web Start (default)"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by packrat on 2011-10-24
to load Scottrader.jnlp just like it does with 11.04! None of the proposed solutions so far work.

---

### Post by drdos2006 on 2011-10-24
Here are a couple of forum replys I have saved for myself.
> 
How to enable Java in Ubuntu
Rated 5 out of 5 stars by Thomas Gutzmann on January 2, 2010
Hi,

here is a short recipe how to enable Java applets and the Java console in Ubuntu (and others with the same installation tool set), compiled from a previous contribution and another hint somewhere:

sudo -i
apt-get update
apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
cd /usr/lib/firefox-addons/extensions
jar -xvf `find /usr/lib/jvm -name ffjcext.zip`
exit

restart Firefox
(normally not required: enable Java)

Hope it helps,

Thomas 

and...
> 
The earlier versions of how to use Firefox with Java to use Webmin are out of 
date.

First of all, java is installed with the Open Office suite. All that is needed, 
and I just did this because I didn't have Java enabled in Firefox, is to go to 
this URL::-- 

[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) 

and when the browser tries to see what version you have, Firefox will alert 
you that it is missing a plugin and that is the IceTea plugin. Allow the 
plugin to install and wait at least 30 seconds for the information to display 
in the testing box.
////////////////////////////////////////////////////////////////////
Alternative
To install the Linux (self-extracting) file
Follow these instructions:

   1. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u<version>-linux-i586.bin
   2. Verify that you have permission to execute the file. Type:
      ls -l

Make sure the installation file has executable permission

   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions.

   4. Run the self-extracting binary Type:
      ./jre-6u<version>-linux-i586.bin

      The license agreement is displayed. Review the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.

   5. Java is installed into its own directory. In this example, it is installed in the /usr/java/jre1.6.0_<version> directory. When the installation has completed, you will see the word Done.

The installation completes

   6. Verify that the jre1.6.0_<version> sub-directory is listed under the current directory. Type:
      ls

Verify the installation filename

The installation is now complete. 
Enable and Configure section.
Firefox or Mozilla

   1. Create a symbolic link to the libjavaplugin.so file in the browser plugins directory
          * Go to the plugins sub-directory under the Firefox installation directory
            cd <Firefox installation directory>/plugins

          * Create the symbolic link
            ln -s <Java installation directory>/plugin/i386/
            ns7/libjavaplugin_oji.so

            In the ln command line above, use ns7-gcc29 if Firefox was compiled with gcc2.9.

      If you install Firefox 1.5 or later, you can enable the Java Console menu item in the Tools menu. Change directories to the Firefox extensions directory, then unzip ffjcext.zip there.

          cd /usr/lib/firefox-1.4/extensions
          unzip /usr/java/jre1.6.0/lib/deploy/ffjcext.zip 

      Example
          * If Firefox is installed at this directory:
            /usr/lib/firefox-1.4/
          * And if the Java is installed at this directory:
            /usr/java/jre1.6.0
          * Then type in the terminal window to go to the browser plug-in directory:
            cd /usr/lib/firefox-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.6.0/plugin/i386/ns7/libjavaplugin_oji.so

   2. Start the Firefox browser, or restart it if it is already up.

      In Firefox, type about:plugins in the Location bar to confirm that the Java Plugin is loaded. If the version is Firefox 1.5 or later, click the Tools menu to confirm that Java Console is there

Test Installation
To test that Java is installed and working properly on your computer, run this test applet.


regards

---

### Post by packrat on 2011-10-24
drdos2006, want to thank you. Personal phobia...don't like command line...much prefer a gui application installer. My best.

---

### Post by drdos2006 on 2011-10-24
Then just use the Package Manager to install Iced-Tea, it is in the repositories.

regards

---

### Post by packrat on 2011-11-05
> **drdos2006 said:**
> Then just use the Package Manager to install Iced-Tea, it is in the repositories.

regards

Did. Still does not work. Thanks.

---

