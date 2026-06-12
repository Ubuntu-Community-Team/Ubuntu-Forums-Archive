---
title: "Cannot use &quot;up&quot; and &quot;down&quot; arrow keys on my keyboard."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by theharshone on 2008-07-01
Hello
I am using Kubuntu Hardy using a svn version of KDE 4.1. When I use it, I cannot use the up and down arrow keys. What is the problem?

Thank you!

---

### Post by cmnorton on 2008-07-01
Can you use the arrow keys in an X-term (command line)?

What does the Section "InputDevice" section look like in /etc/X11/xorg.conf?

---

### Post by theharshone on 2008-07-02
Yes. I can also use them in E17 so i figure its a KDE 4 problem.
Here is the INput from my xorg.conf:

Section "InputDevice"                                                                                                                                                                     
    Identifier     "Generic Keyboard"                                                                                                                                                     
    Driver         "kbd"                                                                                                                                                                  
    Option         "CoreKeyboard"                                                                                                                                                         
    Option         "XkbRules" "xorg"                                                                                                                                                      
    Option         "XkbModel" "hpi6"                                                                                                                                                      
    Option         "XkbLayout" "us"                                                                                                                                                       
EndSection                                                                                                                                                                                
                                                                                                                                                                                          
Section "InputDevice"                                                                                                                                                                     
    Identifier     "Configured Mouse"                                                                                                                                                     
    Driver         "mouse"                                                                                                                                                                
    Option         "CorePointer"                                                                                                                                                          
    Option         "Device" "/dev/input/mice"                                                                                                                                             
    Option         "Protocol" "ImPS/2"                                                                                                                                                    
    Option         "ZAxisMapping" "4 5"                                                                                                                                                   
    Option         "Emulate3Buttons" "true"                                                                                                                                               
EndSection                                        

Thanks!

---

### Post by cmnorton on 2008-07-03
There are only two things things that come to mind. 

1) Using sudo, change Option        "XkbModel"    "pc105" (that's my setting) to different values that make sense.

2) From an X-term (command line) run

sudo dpkg-reconfigure xserver xorg

Accept all defaults, and see what happens when your keyboard is detected.

I have only ever run this from first having logged into the recovery option. That is I have not tried it logged in normally.

---

