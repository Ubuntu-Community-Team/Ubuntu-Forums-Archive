---
title: "sendto() errors"
date: 2010-06-28
forum: Programming Talk
---

### Post by xefix on 2010-06-28
I'm trying to send information to a device that I've connected to by first creating a listening socket, then binding to it. I try to send a string to it using sendto(), which works great until I turn the device off while the program is running. When I do that and attempt to send information to the disconnected device, sendto() gets the following error:

xcb_io.c:249: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <=0)` failed.
Aborted(core dumped)

Is there a way to gracefully circumvent that, or perform some sort of check on whether the device is still connected before attempting the send?

---

### Post by dwhitney67 on 2010-06-28
Well, taking a guess, it appears that you have an assert() statement in your code.  Typically assert() is used for development purposes so that one can be assured that they pass in sane data into a function.

In your case, it is inappropriate to use assert(), because sendto() can fail for reasons beyond your control (as you have already noted).

I would suggest that you re-code the area where the assert() is located to check for the return status of sendto(), and also examine errno.

Alternatively, and I must say this is a "bad" idea, you can disable the assert() by compiling the module where it is located at with the CFLAG -DNDEBUG.  This may cause a failure elsewhere in the code.  The best bet... handle the error where it occurs.

---

### Post by xefix on 2010-06-28
I don't have any assert() statements in my code. I normally check for the return value of sendto(), but in this case, it never even returns (or returns something other than an integer). I am not sure whether it has the chance to reset errno before aborting, but I inserted a print statement after the sendto() call that indicated that errno was set to 22. It still doesn't help me avoid my program's utter failure :sad:

---

### Post by dwhitney67 on 2010-06-28
From the sendto() man-page:
```

RETURN VALUE
       On  success,  these calls return the number of characters sent.  On error, -1 is returned,
       and errno is set appropriately.

```
Check to see if the function returns a -1; if so, then check errno.  Use strerror(), with the value of errno, to get an error string that you might comprehend.
```

#include <string.h>

...

if (sendto(...) == -1)
{
   printf("Error: %s (%d)\n", strerror(errno), errno);
}

```

---

### Post by xefix on 2010-06-28
sendto() appears to return -1, though this is kind of strange because I have if statements to check its return value right after the function call, and the program never seems to make it that far. If I simply print out the return value, however, it comes up with -1. Errno is set to 22: Invalid argument, which could possibly refer to the int socket argument. If this is a normal error, though, why would it abort the entire program as opposed to just returning me an error?

---

### Post by dwhitney67 on 2010-06-28
> **xefix said:**
> sendto() appears to return -1, though this is kind of strange because I have if statements to check its return value right after the function call, and the program never seems to make it that far. If I simply print out the return value, however, it comes up with -1. Errno is set to 22: Invalid argument, which could possibly refer to the int socket argument.

... Or one of the other 5 parameters.  Look at your code carefully, or step through it with a debugger.  If you want, I can take a look at it... but since my psychic powers are weaker during the summer months, I will need for you to post the relevant code.

> **xefix said:**
> 
If this is a normal error, though, why would it abort the entire program as opposed to just returning me an error?
I cannot even speculate at this time.

---

### Post by pbrane on 2010-06-28
The assertion is an X server assertion. dpy is your display. Not sure what the error is or why it appears to be associated with your sendto. xcb is the X protocol C-language Binding. You could try running your program in a debugger with the --sync arg. I assume this is a GUI of some kind. Using gdb you could do a 
```

gdb --args your_program --sync

```

---

### Post by xefix on 2010-06-28
Thanks for the help, guys. Using gdb, I've figured out that the problem wasn't with sendto() after all. There is something wrong with a gtk function I'm using to display the "Unable to send" message. I'll post as soon as I figure out what the deal is.

(btw, --sync isn't working for me. do I need to have special packages installed?)

---

### Post by pbrane on 2010-06-28
> **xefix said:**
> 
(btw, --sync isn't working for me. do I need to have special packages installed?)

As far as I know *--sync* should work with any X client. But you need to use the *--args* with gdb. It's used to do synchronous calls to the X server, easier to debug, but you may not even need it in this case. Do you get an error message?

---

### Post by xefix on 2010-06-28
Hmm...I'm stuck again, though now the program is just segfaulting without any explanation. This is happening when the gtk_dialog_run function calls gdk_window_set_geometry_hints(). I'm new to GTK and haven't quite gotten the hang of it, so it may be something about the way I try to create the message dialog. Here's the function that does this in my code:

void
errNotify(char *message){
   GtkWidget *dialog = gtk_message_dialog_new(0, 0, GTK_MESSAGE_ERROR, GTK_BUTTONS_CLOSE, message);
   gtk_dialog_run(GTK_DIALOG(dialog));
   gtk_widget_destroy(dialog);
}

Whenever I want to display some text from anywhere in my program, I pass the string to errNotify. It works fine normally and only seems to fail when the device is disconnected. I've tried calling it with the exact same message that it fails on at different points in the program, but the dialog box comes up just fine. Does anyone have pointers on what I may be doing wrong here?

EDIT: I apologize for the terrible formatting of the code, but I don't know how to fix it.

---

### Post by pbrane on 2010-06-28
This is probably NOT your issue here but I noticed that the *flags* parameter to *gtk_message_dialog_new* is being called with **0**, I don't know what the behavior of that function is when being called like that but there is no flag that is **0**.
```

typedef enum
{
  GTK_DIALOG_MODAL               = 1 << 0, /* call gtk_window_set_modal (win, TRUE) */
  GTK_DIALOG_DESTROY_WITH_PARENT = 1 << 1, /* call gtk_window_set_destroy_with_parent () */
  GTK_DIALOG_NO_SEPARATOR        = 1 << 2  /* no separator bar above buttons */
} GtkDialogFlags;

```

You might just try setting the *flags* argument to one of these values instead. Unless you know that passing 0 for the flags is acceptable.

Run the program in a debugger set a breakpoint before the *sendto* function, disconnect the device and step through the code. display, watch or print the values of the arguments and variables.

here is a function I wrote similar to yours:
```

void post_message(gchar *msg, gint message_type)
{
	GtkWidget *msg_dialog;

	msg_dialog = gtk_message_dialog_new((GtkWindow *) app,
                                             GTK_DIALOG_DESTROY_WITH_PARENT,
                                             message_type, GTK_BUTTONS_CLOSE, msg);
	gtk_dialog_run(GTK_DIALOG(msg_dialog));
	gtk_widget_destroy(msg_dialog);
}

```

---

### Post by xefix on 2010-06-29
I have tried changing the labels to all of the available options, but nothing seems to work. I wonder if this has anything to do with the fact that I am trying to call my function from a thread, because I've even tried changing the way I display the message (a window with a label instead of a dialog box) and I still get segfaults. I'll post when I have more info.

---

### Post by xefix on 2010-07-29
I abandoned this issue a while ago and just came back to it recently. If anyone is still interested, the reason why I couldn't bring up dialogs directly from threads is because GTK is not thread-safe, and the GUI cannot be safely updated from any thread but the main GUI thread. There is a great explanation and solution for this problem here: [http://tadeboro.blogspot.com/2009/06/multi-threaded-gtk-applications.html](http://tadeboro.blogspot.com/2009/06/multi-threaded-gtk-applications.html)

---

### Post by dwhitney67 on 2010-07-29
> **xefix said:**
> I abandoned this issue a while ago and just came back to it recently. If anyone is still interested, the reason why I couldn't bring up dialogs directly from threads is because GTK is not thread-safe, and the GUI cannot be safely updated from any thread but the main GUI thread. There is a great explanation and solution for this problem here: [http://tadeboro.blogspot.com/2009/06/multi-threaded-gtk-applications.html](http://tadeboro.blogspot.com/2009/06/multi-threaded-gtk-applications.html)

It sure would have been helpful if you had stated from the first post that you are dealing with a multi-threaded application.

Regardless of GTK, there are issues that you need to understand concerning concurrent access to data.

Learn to post better questions, specifically indicating your design and programming proficiency.

... sign off (waiting for a new thread... sigh)

---

