---
title: "Wierd problem: can't click to accept instalation"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by jackswyl on 2012-03-19
Hi everyone, Im new to Ubuntu and Im having some dificulties. The problem occurred when I run the command :
sudo apt-get install --reinstall ubuntu-restricted-extras non-free-codecs libdvdread4 libdvdcss2
The following screen was presented on  my Terminal:
Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                             
 &#9474;                                                                              
 &#9474;                                                                              
 &#9474;                                  <Ok>                 
The problem is: I cant click anywhere to accept it. I searched a solution online and I ran the following command:
sudo dpkg --configure -a && sudo apt-get -f install
This comand brought me back to that screen where I can't click anywhere to accept the terms. Can someone give me a help? Thanks in advance!

---

### Post by winh8r on 2012-03-19
This may be a silly question, but did you use the arrow keys / page down key to "read" the whole agreement and scroll to the end of it. The acceptance tab is at the very end of the agreement.

If you did and there is no accept or Ok button then there is another problem.

---

### Post by grahammechanical on 2012-03-19
When I install this through the Ubuntu Software Centre I get a button to click acceptance of the license.

You are using a terminal you should get back to the prompt with an invitation to enter Y/n for yes or no. It will be at the bottom of the text.

This is my usual experience when using the terminal and it needs my confirmation.

Regards.

---

### Post by wojox on 2012-03-19
<Tab> into it.

---

### Post by jackswyl on 2012-03-19
The <Tab> Trick worked. Thanks a lot guys!

---

