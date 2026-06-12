---
title: "system() error detection C++"
date: 2011-02-28
forum: Programming Talk
---

### Post by sid.mallya on 2011-02-28
I am calling the system() function in my GUI. How do I detect if the command is a success or failure ?

Also, in QT, when I use the 

"connect( ui->pushButton_3, SIGNAL( clicked() ), this, SLOT( browseDir() ) );"

function to browse a directory and open a file, two dialog boxes open in succession. hence, i have to select the files twice or exit the dialog box twice. 

What could be the problem ?

---

### Post by zenwalker on 2011-02-28
I dont have an answer, but just a tip. If you had posted this over QT/KDE forums, you sure would have got the answer pritty fast.

---

### Post by ve4cib on 2011-02-28
In regards to your first question, I refer you to this URL: [http://www.cplusplus.com/reference/clibrary/cstdlib/system/](http://www.cplusplus.com/reference/clibrary/cstdlib/system/)

Basically whenever a program exits it returns an integer (which is why you have "int main() {...}" -- neat, eh?).  The standard is to return 0 if the program completes successfully.  Non-zero values indicate an error of some sort.  I'm not sure if there's a standard for what errors relate to what non-zero values.  I think those are largely application-specific.  I've seen -1 used for critical errors quite a bit.

But for the purposes of your code something like this should work:

```
int ret;
if( !(ret = system("command --with /some/arguments")) ) {
    printf("Command executed normally\n");
}
else {
    printf("Command exited with code %d\n",ret);
}
```

You could also set up a switch statement to deal with different non-zero errors (invalid arguments, i/o errors, segfaults, etc...) if you know what values those use.

All of this obviously hinges on the assumption that whatever program you're calling with system() follows that convention.  Some sloppy programmers will just always return 0 because they don't know any better.  But anything you've written/compiled yourself should follow this (since you can check), and anything that's part of a major set of utilities (i.e. any GNU utils, core Gnome and/or KDE applications, well-maintained services, etc...) will follow this convention.

---

### Post by sid.mallya on 2011-02-28
Thank you for your replies.

@zenwalker,

I actually have registered on the QT Forums but for some reason their confirmation link is not making it to my email ID. Strange .. =/

@ve4cib,

I had tried your advise in a normal c++ test program and it worked like a charm. Unfortunately, in the QT program, the system fails to recognize the following, [I could have made a stupid error. Please correct it, if so]

```
chdir (ui->lineEdit->text().toLocal8Bit().constData());
        strcpy(command1, "text2wave *.txt -o ");
        strcat (command1, dest_name);
        strcat (command1, ".wav");
        if (system(command1))
           ui->label->setText("Error");
        else
            ui->label->setText("Successful converstion to mp3");

```

The compiler fails to recognize the "Error" condition.

---

### Post by sid.mallya on 2011-02-28
Never mind. I got where I was going wrong. =/

---

