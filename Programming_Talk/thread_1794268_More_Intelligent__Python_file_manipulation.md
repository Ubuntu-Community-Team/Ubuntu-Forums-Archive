---
title: "More Intelligent  Python file manipulation"
date: 2011-06-30
forum: Programming Talk
---

### Post by pafoo on 2011-06-30
Trying to find a better way to manage files here is my code snippet
This code works, but to me I think its really sloppy. I am trying to make multiple entries while inputing variables in the middle of a string on one line. then assign that file as a variable and add it to my function mail which is just sendmail function i made with body=""
 
```


##### Lets see if we have any errors in our file... if so lets email that beotch 
#### Otherwise lets append to our server completion list!! then when we reach the last #server email the total list 

message_size = os.stat("/tmp/errors").st_size 

completed_size = os.stat("/tmp/completed").st_size
   
  if message_size != 0:
    messages = open("/tmp/errors", "r")
    message = messages.read()
    messages.close()
    Mail(body=message)
  else:
    if completed_size == 0:
      completed.write("The following servers completed copying logs successfully\n\n")  
      completed.write(server)
      completed.write(" Copied ")
      completed.write(cpy_count)
      completed.write(" out of ")
      completed.write(base_count)
      completed.write(" files. Total size of logs ")
      completed.write(file_sizes)
      completed.write("\n")
    else:
      if server != "final_server_on_list":
        completed.write(server)
        completed.write(" Copied ")
        completed.write(cpy_count)
        completed.write(" out of ")
        completed.write(base_count)
        completed.write(" files. Total size of logs ")
        completed.write(file_sizes)
        completed.write("\n")
      else:
        completed.write(server)
        completed.write(" Copied ")
        completed.write(cpy_count)
        completed.write(" out of ")
        completed.write(base_count)
        completed.write(" files. Total size of logs ")
        completed.write(file_sizes)
        completed.close()
        completed = open("/tmp/completed", "r")
        complete = completed.read()
        Mail(body=complete)
        completed.close()
        completed = open("/tmp/completed", "w")
   
  completed.close()
  
```

---

### Post by juancarlospaco on 2011-06-30
```


##### Lets see if we have any errors in our file... if so lets email that beotch 
#### Otherwise lets append to our server completion list!! then when we reach the last #server email the total list 

message_size = os.stat("/tmp/errors").st_size 

completed_size = os.stat("/tmp/completed").st_size

# declaret that all are Strings so we can concatenate
server = str()
cpy_count = str()
base_count = str()
file_sizes  = str()

  if message_size != 0:
    messages = open("/tmp/errors", "r")
    message = messages.read()
    messages.close()
    Mail(body=message)
  else:
    if completed_size == 0:
      msg = "The following servers completed copying logs successfully\n\n"
      completed.write(msg + server + " Copied " + cpy_count + " out of " + base_count + " files. Total size of logs " + file_sizes + "\n")
    else:
      if server != "final_server_on_list":
        completed.write(server + " Copied " + cpy_count + " out of " + base_count + " files. Total size of logs " + file_sizes + "\n"  )
      else:
        completed.write(server + " Copied " + cpy_count +  " out of " + base_count + " files. Total size of logs " + file_sizes )
        completed.close()
        completed = open("/tmp/completed", "r")
        complete = completed.read()
        Mail(body=complete)
        completed.close()
        completed = open("/tmp/completed", "w")
   
  completed.close()


```

Try this, i hope it works, you can replace all the else if with elif :)
i dont understand what you try to accomplish on the last part of the code, so i dont know.

---

### Post by pafoo on 2011-06-30
Well, at the end what I was doing was after sending off the email I wanted to empty the file so its size would equal 0 again. Essentially this script runs 16 times on 16 different servers, and I want each to append to the file its completion status. That way only 1 email is sent off a day instead of 16 individual. The issue I was having, I tried to cat the files together with + but with python 2.4 I was getting told that .write() takes only 1 argument?

---

### Post by juancarlospaco on 2011-06-30
> **pafoo said:**
> I tried to cat the files together with + but with python 2.4 I was getting told that .write() takes only 1 argument?

OK, so make them become 1 argument only:

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Licence = GPLv3
##### Lets see if we have any errors in our file... if so lets email that beotch 
#### Otherwise lets append to our server completion list!! then when we reach the last #server email the total list 

message_size = os.stat("/tmp/errors").st_size 
completed_size = os.stat("/tmp/completed").st_size

# declaret that all are Strings so we can concatenate
server = str()
cpy_count = str()
base_count = str()
file_sizes  = str()
msg = str("The following servers completed copying logs successfully\n\n")

# Results for Mail Bodys, as 1 argument, String type
equal_zero = str(msg + server + " Copied " + cpy_count + " out of " + base_count + " files. Total size of logs " + file_sizes + "\n")
no_final_srv = str(server + " Copied " + cpy_count + " out of " + base_count + " files. Total size of logs " + file_sizes + "\n")
final_srv = str(server + " Copied " + cpy_count +  " out of " + base_count + " files. Total size of logs " + file_sizes )

  if message_size != 0:
    messages = open("/tmp/errors", "r")
    message = messages.read()
    messages.close()
    Mail(body=message)
  elif completed_size == 0:
      completed.write(equal_zero)
    elif server != "final_server_on_list":
        completed.write(no_final_srv)
      else:
        completed.write(final_srv)
        completed.close()
        completed = open("/tmp/completed", "r")
        complete = completed.read()
        Mail(body=complete)
        completed.close()
        completed = open("/tmp/completed", "w")
   
  completed.close()

```

---

### Post by pafoo on 2011-06-30
Flipin brilliant. Thank you. Not sure why I didn't think of that

---

### Post by juancarlospaco on 2011-06-30
Im just like you but with more time of self-learning, keep it going !

---

### Post by pafoo on 2011-06-30
Thanks, im still a novice in python, but I really love the language! Being a Linux sys admin I came to a point where I was fed up with bash scripting and needed to step it up a notch, and I really didnt like perl's "multiple ways to accomplish a task". So far python has met all my expectations and then some!

---

### Post by juancarlospaco on 2011-06-30
Im senior Linux sys admin too, exact the same...

---

### Post by pafoo on 2011-06-30
Well you said you are self-taught. Thats what ive been having to do. Got any books or sites you recommend? Besides python's doc's =)

---

### Post by juancarlospaco on 2011-06-30
I mainly tend to not learn as usual programmer, maybe because iam admin, but here it goes:

I never done the Python CLI start..., 
i use Ninjas IDE: [http://ninja-ide.org/](http://ninja-ide.org/) (which i help to package)
i go directly to GUI, all my first program work using Bash scripts and os.system('commandhere')
I Started with TKinter from here: infohost.nmt.edu/tcc/help/pubs/tkinter.pdf 
Meanwhile i learned TUI, using This: [http://pythondialog.sourceforge.net/](http://pythondialog.sourceforge.net/)  (nice for Server tasks!)
I never used to like Qt and GTK because i dont like the toolkit sintax, too complex, too much lines.
I have made a lot of Tk mini-apps, small, simple, and to do 1 thing per app (like *nix philosophy say)
Now, im get a little experienced with Python in general..., 
i go for Web!, using this: [http://bottlepy.org/](http://bottlepy.org/) (nice for Intranets small web based apps!)

Now i have my servers with my own PythonDialog admin tools,
running Intranet with my own Bottle web apps.

Try all this on these order, i searched months and months, nothing better or easier i find,
all other stuff are for coders migrating from other language or platform, not for an admin.

Feel free to contact me if you need something...

---

### Post by pafoo on 2011-07-01
Thank you for the information! I will look in to them.

---

