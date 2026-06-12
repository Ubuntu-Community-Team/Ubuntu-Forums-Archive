---
title: "Bash Script For Automation for Skype"
date: 2011-02-16
forum: Programming Talk
---

### Post by ivikas on 2011-02-16
Hi all,

       Iam using skype on ubuntu lucid.I don't see an option in skype on linux that can save the incoming(files that people send you) to our desired location as against the same  options in windows,in which we can browse and save at any location we want.My Skype download folder is 

              ```
/root/SkypeDownloads/Feb_16/
``` 
          (I need to create manually, Folders for each day.)

and edit the skype configuration file to effect this change

This is the location of the config file 

		```
/root/.Skype/your-skype-username/config.xml
```

and this is the string to effect the folder change.

  ```
<LastRecvPath>/root/SkypeDownloads/Feb_16</LastRecvPath>
```


So,i am in need of a bash script that run as the system starts up and do the following

     1.)Check the system date  and create the folder in this location
                           
               ```
 /root/SkypeDownloads/Month-Name_MonthDate

                          for eg: /root/SkypeDownloads/Feb_17
               
```

     2.)Read the skype config file at this location

        ```
/root/.Skype/your-skype-username/config.xml
```

      search for starting **<LastRecvPath>** tag and ending tag **</LastRecvPath>**

        and add the new folder location in step 1 (i.e.,)/root/SkypeDownloads/Feb_17 

        which finally looks like in the config file(
   AS
```
<LastRecvPath>/root/SkypeDownloads/Feb_17</LastRecvPath>
```	

save and exit.

All this when you power on the computer.


I am a new bie in bash scripting,it will be great if some one give an idea on this

Thanks in advance,
vikas

---

