---
title: "python invalid syntax but idontknow what i did wrong?"
date: 2010-04-05
forum: Programming Talk
---

### Post by jakeeee on 2010-04-05
```



#Gmail program

from email.MIMEMultipart import MIMEMultipart
from email.MIMEText import MIMEText

import getpass
import webbrowser
import fileinput
import os
import time
import smtplib
server = smtplib.SMTP('smtp.gmail.com', 587)

server.ehlo()
server.starttls()
server.ehlo()

getpass.unix_getpass()


loop = 1 
 
choice = 0 
 
while loop == 1: 



    #URLS 
    url = ('http://www.gmail.com') 
    url2 = ('https://mail.google.com/mail/?shva=1#inbox')



 
    #Login page 
    print "\nWelcome to Jakes Program.py\n\nPlease login Below: \n" 
    choice = raw_input("Username: ") 
    if choice == 'Jake' 
        choice = raw_input("Password: ")
        if choice == '*******'
            print "Acsess granted :) Welcome Jake.\n"
            server.login("jakejurassic", "********")

        #webbrowser.open_new(url)
                choice = (raw_input("Would you like to read the README.txt before begining?[y/n] ")
                if choice == 'y':
                    print "Opening myREADME.txt...\n"
                    time.sleep(2)
                    os.popen("/usr/bin/gedit")
                    print "Opened.\n"
                    time.sleep(2)
                    print "\nOkay, lets begin. :)"
                    print "What would you like to do?"
                if choice == 'n'
                    print "\nOkay, lets begin. :)"
                    print "What would you like to do?"
                    print " "
                    #Nothing = spotfiller.        
                    print "1. Send a test email."
                    print "2. Read yor mail."
                    print "3. Open your Gmail."
                    print "4. Compose."
                    print "5. exit."                
                    choice = input("Chose the option number: ")

                    if choice == 1:
                        fromaddr = "jakejurassic@gmail.com"
                        toaddr = "jakejurassic@live.com"
                        msg = MIMEMultipart()
                        msg['From'] = fromaddr
                        msg['To'] = toaddr
                        msg['Subject'] = "From my python program"

                        body = "This is a test email coming from jake's python program."
                        msg.attach(MIMEText(body, 'plain'))

                        text = msg.as_string()
                        server.sendmail(fromaddr, toaddr, text)

                        print "Your test email has been sent."


                            if choice == 2:
                                webbrowser.open_new(url2)


                            if choice == 3:
                                webbrowser.open_new(url)


                
                


        else: print "Invalid login info. Please register." 
        raw_input("Press the enter key to exit.") 
 
    loop = 0
```



^^^^^^^^^^^^


Any idea what i did wrong there?

It says the error is in " if choice == 'Jake' "

---

### Post by skierkyles on 2010-04-05
You forgot the ":" after a few of your if statements :)

---

### Post by jakeeee on 2010-04-05
> **skierkyles said:**
> You forgot the ":" after a few of your if statements :)


Wow lol i feel a little stupid Dx

Thanks so much :D

---

