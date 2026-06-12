---
title: "TIPS ON: How to get out of package installation jams offline."
date: 2007-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Masterj15 on 2007-03-22
This is a help guide on how to get out of those fustrating package Jams that people go through when your using Gbedi package manager offline. This is more for people off line beacuse if you had internet for that computer then you would not need Gbedi, you would just use synaptic and you would just download all the things you need without having to go to your source of internet and keep downloading things.

Numero uno: If your downloading some packages off the internet from [www.debian](www.debian). org or [www.Ubuntupackages.com](www.Ubuntupackages.com) make sure to download their dependencies (Which are the ones with the red dot before you scroll do to your download.) I this how it would work.


                                                     Package you wanted

                                             Packages you need to download 
                                                              
                               Those packages you need to download for the second line

                So on and so on until the great day when you don't need anymore packages



Number two: If you want to get rid off a package that you downloaded go to synaptic package manager and search for the package that you are wishing to delete. Or you can go into the search filter and look so a section that says local or obsolete to find all the packages you installed through Gbedi. If your package says that if will delete some things of your compture that you need to keep your lovely ubuntu working then you will have to remove the package by terminal. Go to the terminal and type in sudo aptitude. This will enable the terminal package manger. Type in / to search for you package that you want to delete then when you found it press - to highlight it to delete off off your computer completely and download to the origonal product.

But what if there is not any downgrade?
Then you will have to do this the hard way. You will have to wright down every signal package that they have deleted before the process begins so you can redownload them. Make sure nothing happens to your computer during this process and make sure you have either your live ubuntu disk or the non live ubuntu disk. Delete the package and it will automaticly delete the other packages. When you are done search in aptitude for all the packages and press + to install them again. If you need help type in ? in the aptitude for assiant commands that you are looking for. 

This will be edited in the near future for question, answeres, statements, and more info on this matter.

---

