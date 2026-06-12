---
title: "Installing  Sun JRE (Java Run-time Environment ) in Ubuntu"
date: 2011-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by manishraj2011 on 2011-05-21
[SIZE=3][COLOR=Red]# Steps to install Sun JRE :[/COLOR][/SIZE]

1) Download the bin file ( Linux self-extracting ) from here  :

   [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

2) make the file executable :

    ```
chmod u+x <file>
```

3)  Get the root access : 

   ```
sudo -s
```

   ( It will prompt for your password  )

4) Go to /usr directory :

  ```
cd /usr
```

5) Make a directory named java 

   ```
mkdir java
```

6) Go to the java directory :

    ```
cd java
```

7) run the downloaded file with full path :

   e.g. ```
/home/user_name/Downloads/jre-6u25-linux-i586.bin
```

[SIZE=3][COLOR=Red]# Additional Steps to install firefox-4.0 plugin[/COLOR][/SIZE]

8) Go to firefox plugin directory :

   ```
cd /usr/lib/firefox-4.0/plugins/
```

9) Create a link for the plugin :

   ```
ln -s /usr/java/jre1.6.0_24/lib/i386/libnpjp2.so
```

10) For confirming the installation of plugin, close all firefox windows and re-open it .

    Type in :

     ```
about:plugins
```

    in the awesome bar ( as firefox calls it    )  and pressing enter key .

11) You can also confirm the installation of java plugin by the following link :

     [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)




Courtesy : [http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)

---

