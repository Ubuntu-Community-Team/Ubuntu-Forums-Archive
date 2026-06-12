---
title: "help me in learning glade and c ....."
date: 2007-07-14
forum: Programming Talk
---

### Post by @vijay@ on 2007-07-14
i recently started to work with glade ....... its a nice tool for writing gui applications 
but im facing a few problems

i have a few questions

1)how can i display the terminal output to a text widget  in glade (or) store the output of the command to a string?
for example 
popen("tcprobe -i input avi file | grep \"Video:\"","r");

tcprobe -i input avi file | grep "Video:","r"
output's something like video: .........
i want this to be stored in a string in c or displayed in a text widget in glade

2)how can i use variables in popen() command   ;     at present im using strcat() to join the variables and others  and then using    popen(finalvariable,"r")

3)how to use terminal variables in c program???
  for example i executed the a terminal command using popen
  popen("total_value = `12345`","r");
  now i want to access the variable tatal_value in the c code

  in shell scripts we use $total_value whats its equivalent in c????

4)when i open the compiled glade application in terminal , i can see whats going behind the application ; when i doudle click and directly opens the file i cant see any information
is it possible to display this log information on a button click in glade application??

sorry for my poor english

---

### Post by daou on 2007-07-14
2) You can't use formatted strings with arguments inside the popen command. You will have to use an extra variable to hold the string. One way is to do it with strcat. If you want to use a formatted string, you can use sprintf.

But if you are using Gtk, I highly suggest you look at Glib's string utilities [http://developer.gnome.org/doc/API/2.0/glib/glib-String-Utility-Functions.html](http://developer.gnome.org/doc/API/2.0/glib/glib-String-Utility-Functions.html)

Then you can use functions like g_strdup_printf("format string", format args) to automatically allocate the variable with the correct info (and it's safer that sprintf).

1) I assume you know how to read the pipe opened by popen(). Then store all the info in a string and use that string to set the text of a widget (like a label or text box). The [Gtk+ reference manual]("http://developer.gnome.org/doc/API/2.0/gtk/index.html") is your friend.

3) Are you trying to set an environment variable? If so, you should just use the setnv(), unsetenv(), and getenv() functions in C to set, unset, and read them.

Also, are you aware of the differences between popen(), system, and the various exec() functions?

[http://www.die.net]("http://www.die.net/") is an excellent reference for all the Linux C commands.

4) I'm a bit unclear about what you are trying to do here.

---

### Post by slavik on 2007-07-14
I suggest taking a look at hotwire.

---

### Post by @vijay@ on 2007-07-16
@daou
thanx for the information very usefull :)

1) the problem is i stored the pipe opened by popen in a string but im unable to figure out how to display this text to gtktextviewer widget
if it is a gtkentry i can simply use some thing like gtk_set_text ...
when i open help for gtktextviewer
there is no such command for it  ...... 
there is something about buffers ..... im unable to understand

3)ye thats what im trying to do thanx a lot

4)wht im trying to do is
when i open the executable file created after compiling the c files from terminal like
$ cd folder
$ ./executable
i can see message in terminal displaying any failures in executing any command etc....

when i open the executable file just by double clicking on it i cant see these massages

wht i want to is create a button on the application so when i click that button i can view these messages in a textviewerwidget or in another terminal 




one more thing .......... 

what is the use for popen("command","w"); how is it usefull??

---

### Post by @vijay@ on 2007-07-24
recently i have heard of vte terminal widget 

can anyone provide more info??? how can i use it in glade

---

### Post by daou on 2007-07-25
> **@vijay@ said:**
> @daou
thanx for the information very usefull :)

1) the problem is i stored the pipe opened by popen in a string but im unable to figure out how to display this text to gtktextviewer widget
if it is a gtkentry i can simply use some thing like gtk_set_text ...
when i open help for gtktextviewer
there is no such command for it  ...... 
there is something about buffers ..... im unable to understand

3)ye thats what im trying to do thanx a lot

4)wht im trying to do is
when i open the executable file created after compiling the c files from terminal like
$ cd folder
$ ./executable
i can see message in terminal displaying any failures in executing any command etc....

when i open the executable file just by double clicking on it i cant see these massages

wht i want to is create a button on the application so when i click that button i can view these messages in a textviewerwidget or in another terminal 




one more thing .......... 

what is the use for popen("command","w"); how is it usefull??

popen is used to execute a program and open a pipe (one way communication channel) between that program and your program. Then you can either read from that pipe, getting all the output from the program, or write to the pipe, to give the program input. But you can't both read and write from the same process using the same pipe.

Using the text boxes is a little bit difficult at first because of the buffers. I suggest you find some source code for another program and see how they do it. I have some code somewhere using the text boxes but can't find it at the moment.

One way to get all output from a program's stdout and stderr,is to redirect those streams somewhere else. You can close the streams, stdout and stderr, then open your own streams and save stream pointers in stdout and stderr. 
Then read that stream and dump all output to a text box. There might be an easier way, such as opening a terminal in a widget. I've never done this before, so I can't be certain.

---

### Post by @vijay@ on 2007-07-31
THANX ALOT DAOU:):)

ok i was able to display text in textviewer by the following code
GtkTextBuffer * buffer;
buffer = gtk_text_view_get_buffer (GTK_TEXT_VIEW(outputtextviewerwidget));
gtk_text_buffer_set_text (buffer,"hello",-1);

i can redirect the stdout and stderr to a file using
freopen("log.log", "w", stdout); // redirect stdoutput to a file 
freopen("log.log", "w", stderr); // redirect stdoutput to a file 

but how can i redirect them to a textviewer widget ????????

---

