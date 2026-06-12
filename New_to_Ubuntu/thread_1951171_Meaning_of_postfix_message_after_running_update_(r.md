---
title: "Meaning of postfix message after running update (regarding auto-apt)?"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-02
[FONT=Arial][SIZE=2]I'm trying to take care of some of the dependencies issues after upgrading to 11.04. I just ran the following command (which apparently downloaded a series of updates): [/SIZE][/FONT]

           sudo apt-get install auto-apt

[FONT=Times New Roman][SIZE=2][FONT=Arial]and got the message (below) in Terminal. The message seems 
to take over the Terminal; it asks for a choice to be made, but offers no 
interactivity that I can see; pressing spacebar, hitting return does 
nothing[U].

I'm wondering what I'm supposed to do from that point forward, 
since the shell won't respond, and I seem to be left with no option other 
than to exit the Terminal):[/U] [/FONT]
[/SIZE][/FONT]
&#9474; Please select the mail server configuration type that best meets your     
  &#9474; needs.                                                                    
  &#9474;                                                                           
  &#9474;  No configuration:                                                        
  &#9474;   Should be chosen to leave the current configuration unchanged.          
  &#9474;  Internet site:                                                           
  &#9474;   Mail is sent and received directly using SMTP.                          
  &#9474;  Internet with smarthost:                                                 
  &#9474;   Mail is received directly using SMTP or by running a utility such       
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                  
  &#9474;  Satellite system:                                                        
  &#9474;   All mail is sent to another machine, called a 'smarthost', for          
  &#9474; delivery.                                                                 
  &#9474;  Local only:                                                              
  &#9474;                                                                           
  &#9474;                                 <Ok>

---

### Post by lechien73 on 2012-04-02
Have you tried using the arrow keys, or tab key? Normally this prompt is waiting for you to select a mail configuration, and a cursor or selection bar should be visible on the screen.

---

### Post by jps2012 on 2012-04-02
[lechien73]("http://ubuntuforums.org/member.php?u=1031904"): You saved me. I hadn't tried using the arrow keys (not the right/left keys). I'd only tried to scroll through the text with the up/down keys. 

I followed your advice, made a choice in the terminal, and then auto-update finished running. MANY, many thanks.

---

