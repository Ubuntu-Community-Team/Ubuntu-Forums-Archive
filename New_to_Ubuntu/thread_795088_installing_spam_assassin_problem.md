---
title: "installing spam assassin problem"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by furoido on 2008-05-15
Trying to install/activate spam assassin for evolution and get this:


andrew@andrew-desktop:~$ apt-get install spamassassin
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


What do I do next?! Or am I going aboput it the wrong way? (Evolution tells me it can't install the plugins and to check if the package is intalled)

PS If you think there are better spam filters that spam assassin that are really easy to install, please let me know!

---

### Post by Trail on 2008-05-15
sudo apt-get install spamassassin

---

### Post by furoido on 2008-05-15
Sorry Trail, I'm a complete beginner and don't know what you mean by code or where to type it in! Be grateful if you could explain in idiot-language!! Thanks!

---

### Post by CryptiniteDemon on 2008-05-15
Type Alt + F2
Type in gnome-terminal
Hit enter
copy that code
past it in the terminal (ctrl + shift + v)
hit enter

---

### Post by argraff on 2008-05-15
The term 'sudo' is for 'super-user do' - meaning root. This allows you to have the permission to perform system-altering commands. You put it in front of commands that need root permissions. Just be careful, there is no undo! :)

When I was starting out, I never used it until the computer would ask me if I was root. Then I knew to be careful of my typing. Now, I've got a handle on it...It'll come with time.

---

### Post by furoido on 2008-05-15
did it and got this!

ndrew@andrew-desktop:~$ banner -w 50 Trail
                                        ###### 
                                        ###### 
                                           ### 
                                            ## 
                                             # 
            #                                # 
            #                                # 
            ################################## 
            ################################## 
            ################################## 
            #                                # 
            #                                # 
                                             # 
                                            ## 
                                            ## 
                                        ###### 
                                        ###### 
            #                  # 
            #################### 
            #################### 
            #################### 
            #             ###
                            ## 
                             ## 
                             ###
                         ####### 
                         ####### 
                         #######
                              
                ### 
              ########
             ##########   ##### 
            ####    ####  ######
            ##        ##      ## 
            ##        ##       # 
             ##      ##       ## 
              ##################
            ###################
            ##################
            ## 
            #
            #                  # 
            ####################      ### 
            ####################     ##### 
            ####################     #####
            # 
            #                                # 
            ################################## 
            ################################## 
            ################################## 
            # 
andrew@andrew-desktop:~$

---

### Post by Ejas12 on 2008-05-26
No, the code he wanted you to enter is the first one:
**sudo apt-get install spamassassin**

the ap-get install is what the order to install anything, and you need the permisions to do this (that is why you use sudo at the beginning)

---

