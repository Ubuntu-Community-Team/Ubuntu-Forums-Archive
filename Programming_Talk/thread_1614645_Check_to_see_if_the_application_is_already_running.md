---
title: "Check to see if the application is already running! C/C++ - Nice way"
date: 2010-11-05
forum: Programming Talk
---

### Post by hakermania on 2010-11-05
There is always the way to check for a file at application start, and if not found to create it and launch  the program normally, and if found to say that the program is already running! And then on the close of the program to delete this file.
So you start the program, the file is created, and if another try of launching the program is made then you find the file, so you say that the program is currently running!
But this have a very big disadvantage! If your program force quits, then the file won't be deleted, and so the application would not be able to be launched unless the file is deleted by hand (something that can be done usually only by experts of the specific program)!
So, I figured out a better solution. the code is in C++ using QtCreator:
```

char p=getenv("USER");
system("pidof MyApp > /home/$USER/.config/MyApp/Checks/concurrent; launched=`awk '{print NF-1}' /home/$USER/.config/MyApp/Checks/concurrent`; if [ $launched -ne 0 ]; then echo \"Close\" > /home/$USER/.config/MyApp/Checks/concurrent; fi");
    char homepid[150]="/home/";
    strcat(homepid,p);
    char otherpid[100]="/.config/MyApp/Checks/concurrent";
    strcat(homepid,otherpid);
    char linepid [ 128 ];
    int ipid;
   FILE *filepid = fopen ( homepid, "r" );
       for ( ipid = 0; ipid < 1; ++ipid ) //getting the first line...
       {
       fgets ( linepid, sizeof linepid, filepid );
    }

   fclose ( filepid );
   if(!strcmp (linepid,"Close\n")){system("echo \"\" > /home/$USER/.config/MyApp/Checks/concurrent"); QMessageBox::information(0, "Error!", "MyApp is already running!");};

```
What this source actually does is to check how many spaces does the pidof <MyApp> has!
pidof MyApp gives all the IDs of the process(es) named MyApp, so if they are 2, one space will exist etc. So, i check the number of spaces and if found something else than zero then it says that the program is allready running :) Simple I think :)

---

### Post by Arndt on 2010-11-06
> **hakermania said:**
> There is always the way to check for a file at application start, and if not found to create it and launch  the program normally, and if found to say that the program is already running! And then on the close of the program to delete this file.
So you start the program, the file is created, and if another try of launching the program is made then you find the file, so you say that the program is currently running!
But this have a very big disadvantage! If your program force quits, then the file won't be deleted, and so the application would not be able to be launched unless the file is deleted by hand (something that can be done usually only by experts of the specific program)!
So, I figured out a better solution. the code is in C++ using QtCreator:
```

char p=getenv("USER");
system("pidof MyApp > /home/$USER/.config/MyApp/Checks/concurrent; launched=`awk '{print NF-1}' /home/$USER/.config/MyApp/Checks/concurrent`; if [ $launched -ne 0 ]; then echo \"Close\" > /home/$USER/.config/MyApp/Checks/concurrent; fi");
    char homepid[150]="/home/";
    strcat(homepid,p);
    char otherpid[100]="/.config/MyApp/Checks/concurrent";
    strcat(homepid,otherpid);
    char linepid [ 128 ];
    int ipid;
   FILE *filepid = fopen ( homepid, "r" );
       for ( ipid = 0; ipid < 1; ++ipid ) //getting the first line...
       {
       fgets ( linepid, sizeof linepid, filepid );
    }

   fclose ( filepid );
   if(!strcmp (linepid,"Close\n")){system("echo \"\" > /home/$USER/.config/MyApp/Checks/concurrent"); QMessageBox::information(0, "Error!", "MyApp is already running!");};

```
What this source actually does is to check how many spaces does the pidof <MyApp> has!
pidof MyApp gives all the IDs of the process(es) named MyApp, so if they are 2, one space will exist etc. So, i check the number of spaces and if found something else than zero then it says that the program is allready running :) Simple I think :)

What could be the defence of this construction?

```
       for ( ipid = 0; ipid < 1; ++ipid ) //getting the first line...
 
```

I didn't really understand your method, but one way often used is to write ones own pid into the file. The next invocation checks whether there is a process running with that pid. Occasionally, a completely unrelated process may be running with the same pid, of course.

---

### Post by hakermania on 2010-11-06
Ok, it will maybe be a strange way of reding a file, you're right :/
Your method is good, but what if the program force quits, or the PC shutdowns unexpectedly or something else? The file with the ID written on it will not be deleted and so the program will not be able to start again because it will see that  the file exists. :)
With my method there is no such possibility! The pidof checks in real time whether there is a running application and writes the results in a file. Then tthe programs read the file and if it find more than 0 spaces it doesn't allow it to ruun :)

---

### Post by Arndt on 2010-11-06
> **hakermania said:**
> Ok, it will maybe be a strange way of reding a file, you're right :/
Your method is good, but what if the program force quits, or the PC shutdowns unexpectedly or something else? The file with the ID written on it will not be deleted and so the program will not be able to start again because it will see that  the file exists. :)
With my method there is no such possibility! The pidof checks in real time whether there is a running application and writes the results in a file. Then tthe programs read the file and if it find more than 0 spaces it doesn't allow it to ruun :)

The point of storing the pid in the file is to check whether a process with just that pid is running.

As for "for ( ipid = 0; ipid < 1; ++ipid )", you can strike that line out: it runs exactly once.

---

### Post by hakermania on 2010-11-07
Ok thx for the corrections on the code. I posted it because I've readen a lot of articles having the dilemma whether or not to choose to do the way with the file, so I think that's a better solution :)

---

