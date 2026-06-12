---
title: "Easygui Issue ( opens a command prompt and program)"
date: 2008-04-15
forum: Programming Talk
---

### Post by jseiser on 2008-04-15
[PHP]import easygui, sys, telnetlib, time
while True:
    vpc = easygui.enterbox(message='Enter VCI.', title='Enter VCI', argDefaultText='')
    if vpc == 'None':
        sys.exit()
    if vpc[0] in ('1', '2'):
        vpc = vpc[0] + '01' + vpc[2:]
        HOST = "0.0.0.0"
        password = "password"
        tn = telnetlib.Telnet(HOST)
        tn.read_until("Password: ")
        tn.write(password + "\n")
        tn.write("sh int atm6/0." + str(vpc) + "\n")
        tn.write("sh arp | in " + str(vpc) + "\n")
        tn.write("exit\n")
        outstring = tn.read_all()
        #print tn.read_all()
        #time.sleep(10)
        #sys.exit(0)
        easygui.codebox(message='Results' , title='VCI Results', text=outstring)
    else:
        #print "Wrong Server ( 3/ VPI ) or invalid VCI"
        easygui.textbox(message='Error', title='ERROR', text='Wrong Server ( 3/ VPI ) or invalid VCI', codebox=0)
        time.sleep(1)
[/PHP]

This works, but it also opens a command prompt in the background.  I open the program by just running the .py file from the desktop ( ug, this damn windows pc at work )

---

### Post by LaRoza on 2008-04-15
Change the extension to .pyw

---

### Post by jseiser on 2008-04-15
heh, thanks :)

---

### Post by LaRoza on 2008-04-15
> **jseiser said:**
> heh, thanks :)

It worked?

---

