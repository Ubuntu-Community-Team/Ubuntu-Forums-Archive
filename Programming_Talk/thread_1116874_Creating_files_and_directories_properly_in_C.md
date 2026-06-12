---
title: "Creating files and directories properly in C"
date: 2009-04-05
forum: Programming Talk
---

### Post by PmDematagoda on 2009-04-05
I was wondering if there was a "standard" way of creating files or directories using C, especially if they were for configuration files for an application. I've managed to come up with this code(whole code is about 750+ lines):-
```
int main(int argc, char *argv[]){
  unsigned int time_elapse;
  int test_fd;
  DIR *test_dir;
  char *path;

  /* We first allocate the amount of memory required for the configuration directory and file.*/
  path = (char *) malloc( (strlen(getenv("HOME")) + strlen("/.reminder_config_temp/reminder.conf")) * sizeof(char) );

  /* We then obtain the home directory of the user running the application.*/
  strcpy(path,getenv("HOME"));

  /* We then concatanate the required directory.*/
  strcat(path,"/.reminder_config_temp/");

  /* The directory path is tested to see if it exists, if it doesn't, we create it.*/
  if( (test_dir = opendir(path)) == NULL ){

    /* If mkdir() returns 1, we handle the error.*/
    if( mkdir(path,S_IRWXU) ){
      printf("Error %d: %s\n"						\
	     "Unable to create configuration directory \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
    }
  }
  /* If everything went alright, we close the directory stream.*/
  else
    closedir(test_dir);

  /* The configuration filename is then concatanated.*/
  strcat(path,"reminder.conf");

  /* If the file does not exist, it is created.*/
  if (access(path, F_OK)){

    if( ( test_fd = open(path, O_RDWR | O_CREAT | O_EXCL, S_IRUSR | S_IWUSR) == -1)){
      printf("Error %d: %s\n"						\
	     "Unable to access configuration file \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
    }
    /* Upon succesful creation, the file descriptor is closed.*/
    else
      close(test_fd);
  }

  gtk_init(&argc,&argv);

  time_elapse = time_check(path);
  
  action_decider(time_elapse,path);

  alarm_daemon(time_elapse);

  ui_popup(&argc,argv,path);

  return 0;
}
```

So mainly what I'm wondering is, have I done it right?

Any help is appreciated.:)

---

### Post by dwhitney67 on 2009-04-05
It looks ok to me, although you really should check that getenv("HOME") returns a valid pointer, otherwise your program will crash.

Btw, in lieu of opendir() and closedir(), you can consider using stat().

---

### Post by nvteighen on 2009-04-05
Well, directories are filesystem specific, so it will never be cross-platform...

---

### Post by PmDematagoda on 2009-04-05
> **nvteighen said:**
> Well, directories are filesystem specific, so it will never be cross-platform...

Well, I'm not really looking for cross-platform at the moment.:)

> **dwhitney67 said:**
> It looks ok to me, although you really should check that getenv("HOME") returns a valid pointer, otherwise your program will crash.

Btw, in lieu of opendir() and closedir(), you can consider using stat().

Thanks for pointing that out, I changed the code accordingly:-
```
int main(int argc, char *argv[]){
  unsigned int time_elapse;
  int test_fd;
  DIR *test_dir;
  char *path,*home_dir;

  [COLOR="Red"]if( (home_dir = getenv("HOME")) == NULL){
    printf("Unable to find the location of the home directory.\n"
	   "Please set the HOME environment variable properly and run this program again.\n");
    return 1;
  }[/COLOR]
  /* We first allocate the amount of memory required for the configuration directory and file.*/
  path = (char *) malloc( (strlen(home_dir) + strlen("/.reminder_config_temp/reminder.conf")) * sizeof(char) );

  /* We then obtain the home directory of the user running the application.*/
  strcpy(path,home_dir);

  free(home_dir);

  /* We then concatanate the required directory.*/
  strcat(path,"/.reminder_config_temp/");

  /* The directory path is tested to see if it exists, if it doesn't, we create it.*/
  if( (test_dir = opendir(path)) == NULL ){

    /* If mkdir() returns 1, we handle the error.*/
    if( mkdir(path,S_IRWXU) ){
      printf("Error %d: %s\n"						\
	     "Unable to create configuration directory \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
    }
  }
  /* If everything went alright, we close the directory stream.*/
  else
    closedir(test_dir);

  /* The configuration filename is then concatanated.*/
  strcat(path,"reminder.conf");

  /* If the file does not exist, it is created.*/
  if (access(path, F_OK)){

    if( ( test_fd = open(path, O_RDWR | O_CREAT | O_EXCL, S_IRUSR | S_IWUSR) == -1)){
      printf("Error %d: %s\n"						\
	     "Unable to access configuration file \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
    }
    /* Upon succesful creation, the file descriptor is closed.*/
    else
      close(test_fd);
  }

  gtk_init(&argc,&argv);

  time_elapse = time_check(path);
  
  action_decider(time_elapse,path);

  alarm_daemon(time_elapse);

  ui_popup(&argc,argv,path);

  return 0;
}
```
and stat() is more efficient that using opendir() and closedir(), so I will make the changes sometime soon.:)

---

### Post by PmDematagoda on 2009-04-07
So I've replaced closedir() and opendir() with stat(), the new code is:-
```
int main(int argc, char *argv[]){
  unsigned int time_elapse;
  int test_fd,stat_no;
  DIR *test_dir;
  struct stat test_buf;
  char *path,*home_dir;

  if( (home_dir = getenv("HOME")) == NULL){
    printf("Unable to find the location of the home directory.\n"
	   "Please set the HOME environment variable properly and run this program again.\n");
    return 1;
  }
  /* We first allocate the amount of memory required for the configuration directory and file.*/
  path = (char *) malloc( (strlen(home_dir) + strlen("/.reminder_config_temp/reminder.conf")) * sizeof(char) );

  /* We then obtain the home directory of the user running the application.*/
  strcpy(path,home_dir);

/*   free(home_dir); */

  /* We then concatanate the required directory.*/
  strcat(path,"/.reminder_config_temp");

[COLOR="Red"]  stat_no = stat(path,&test_buf);

  if ( stat_no == -1 && ( errno == ENOENT )){
    if( mkdir(path,S_IRWXU) ){
      printf("HE");
      printf("Error %d: %s\n"						\
	     "Unable to create configuration directory \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
    }
  }
  
  else if(stat_no == 0){

    switch (test_buf.st_mode & S_IFMT){
      
    case S_IFDIR:
      break;
      
    default:
    printf("A filesystem object(e.g a file) already has the same name as the configuration folder:-\n"
	   "%s\n"
	   "Please resolve this conflict and try again.\n",path);
    exit(0);
    }
  }
  
  else{
    printf("%d\n",stat_no);
      printf("Error %d: %s\n"						\
	     "Unable to create configuration directory \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
  }[/COLOR]
 /*  /\* The directory path is tested to see if it exists, if it doesn't, we create it.*\/ */
/*   if( (test_dir = opendir(path)) == NULL ){ */

/*     /\* If mkdir() returns 1, we handle the error.*\/ */
/*     if( mkdir(path,S_IRWXU) ){ */
/*       printf("Error %d: %s\n"						\ */
/* 	     "Unable to create configuration directory \"%s\", please check permissions.\n",errno, strerror(errno),path); */
/*       exit(errno); */
/*     } */
/*   } */
/*   /\* If everything went alright, we close the directory stream.*\/ */
/*   else */
/*     closedir(test_dir); */

  /* The configuration filename is then concatanated.*/
  strcat(path,"/reminder.conf");

  /* If the file does not exist, it is created.*/
  if (access(path, F_OK)){

    if( ( test_fd = open(path, O_RDWR | O_CREAT | O_EXCL, S_IRUSR | S_IWUSR) == -1)){
      printf("Error %d: %s\n"						\
	     "Unable to access configuration file \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
    }
    /* Upon succesful creation, the file descriptor is closed.*/
    else
      close(test_fd);
  }

  gtk_init(&argc,&argv);

  time_elapse = time_check(path);
  
  action_decider(time_elapse,path);

  alarm_daemon(time_elapse);

  ui_popup(&argc,argv,path);

  return 0;
}
```

So I would like to ask, is my use of stat() in the above code correct?

Thanks in advance.:)

---

### Post by dwhitney67 on 2009-04-07
Perhaps you are making it more complicated than necessary.  Your ultimate goal is to create a configuration file within a particular directory.

If the directory does not exist, create it.  Two things can happen here:  either you succeed or you fail.  If you succeed, then you can create the file; otherwise you cannot... end of story.

Here's some code to demonstrate the scenario above:
```

#include <sys/stat.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>


int main(int argc, char** argv)
{
  const char* REMINDER_DIR  = "/.reminder_config_temp/";
  const char* REMINDER_FILE = "reminder.conf";
  const char* HOME_DIR      = getenv("HOME");

  if (!HOME_DIR)
  {
    fprintf(stderr, "HOME environment variable is not defined.\n");
    return 1;
  }

  char* path = malloc(strlen(HOME_DIR) + strlen(REMINDER_DIR) + strlen(REMINDER_FILE) + 1);

  sprintf(path, "%s%s", HOME_DIR, REMINDER_DIR);

  struct stat buf;

  if (stat(path, &buf) != 0)
  {
    // directory does not exist; attempt to create it
    if (mkdir(path, S_IRWXU) != 0)
    {
      // failure
      printf("failure... unable to create directory %s.\n", path);
      return 2;
    }
  }

  // ultimate goal is to create a file within path dir;
  // if we reach this point, it should be possible.
  strcat(path, REMINDER_FILE);

  printf("success... will create file %s...\n", path);

  free(path);

  return 0;
}

```
P.S.  The code above is written using gnu99 standards.

---

### Post by PmDematagoda on 2009-04-07
> **dwhitney67 said:**
> Perhaps you are making it more complicated than necessary.  Your ultimate goal is to create a configuration file within a particular directory.

If the directory does not exist, create it.  Two things can happen here:  either you succeed or you fail.  If you succeed, then you can create the file; otherwise you cannot... end of story.

Here's some code to demonstrate the scenario above:
```

#include <sys/stat.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>


int main(int argc, char** argv)
{
  const char* REMINDER_DIR  = "/.reminder_config_temp/";
  const char* REMINDER_FILE = "reminder.conf";
  const char* HOME_DIR      = getenv("HOME");

  if (!HOME_DIR)
  {
    fprintf(stderr, "HOME environment variable is not defined.\n");
    return 1;
  }

  char* path = malloc(strlen(HOME_DIR) + strlen(REMINDER_DIR) + strlen(REMINDER_FILE) + 1);

  sprintf(path, "%s%s", HOME_DIR, REMINDER_DIR);

  struct stat buf;

  if (stat(path, &buf) != 0)
  {
    // directory does not exist; attempt to create it
    if (mkdir(path, S_IRWXU) != 0)
    {
      // failure
      printf("failure... unable to create directory %s.\n", path);
      return 2;
    }
  }

  // ultimate goal is to create a file within path dir;
  // if we reach this point, it should be possible.
  strcat(path, REMINDER_FILE);

  printf("success... will create file %s...\n", path);

  free(path);

  return 0;
}

```
P.S.  The code above is written using gnu99 standards.

Point made.:) 

However, if my intention was to be as transparent to the user as possible and try and give informative error messages, would my code be in order?

---

### Post by dwhitney67 on 2009-04-07
Your code will work; I never stated otherwise.  I just think it is a bit complicated/overzealous for a trivial task.

For instance, you check for 3 possible scenarios after calling stat(), with one scenario employing a switch.  Why is that?

stat() is pretty smart; it knows whether you are looking for a file or for a directory, based on the last character of the path that is provided.  In my example, I defined REMINDER_DIR with a trailing '/' character for just that purpose, and also to assist in the effort to allocate the appropriate space for the variable 'path'.

If your application can create a directory, I assure you, you *should* also be able to create a file within that directory.  I used the word "should", because Linux is a multi-tasking OS, and it is possible that after you successfully stat() or mkdir() a directory, that it could disappear on you prior to performing an fopen() (btw, I never use open() unless I am doing low-level I/O).

In the event that you cannot create the file, then you report such error.  The directory will exist either before or after you create it, and if not, then you notify the user of the appropriate error with your attempt to create it.

---

### Post by PmDematagoda on 2009-04-07
> **dwhitney67 said:**
> Your code will work; I never stated otherwise.  I just think it is a bit complicated/overzealous for a trivial task.

For instance, you check for 3 possible scenarios after calling stat(), with one scenario employing a switch.  Why is that?

stat() is pretty smart; it knows whether you are looking for a file or for a directory, based on the last character of the path that is provided.  In my example, I defined REMINDER_DIR with a trailing '/' character for just that purpose, and also to assist in the effort to allocate the appropriate space for the variable 'path'.

If your application can create a directory, I assure you, you *should* also be able to create a file within that directory.  I used the word "should", because Linux is a multi-tasking OS, and it is possible that after you successfully stat() or mkdir() a directory, that it could disappear on you prior to performing an fopen() (btw, I never use open() unless I am doing low-level I/O).

In the event that you cannot create the file, then you report such error.  The directory will exist either before or after you create it, and if not, then you notify the user of the appropriate error with your attempt to create it.

Thank you for the explanation, I agree with what was said.:)

So now the code looks like this:-
```
int main(int argc, char *argv[]){
  unsigned int time_elapse;
  int test_fd;
  struct stat test_buf;
  char *path,*home_dir;

  if( (home_dir = getenv("HOME")) == NULL){
    printf("Unable to find the location of the home directory.\n"
	   "Please set the HOME environment variable properly and run this program again.\n");
    return 1;
  }
  /* We first allocate the amount of memory required for the configuration directory and file.*/
  path = (char *) malloc( (strlen(home_dir) + strlen("/.reminder_config_temp/reminder.conf")) * sizeof(char) );

  /* We then obtain the home directory of the user running the application.*/
  strcpy(path,home_dir);

  /* We then concatanate the required directory.*/
  strcat(path,"/.reminder_config_temp/");

  if ( stat(path,&test_buf) != 0 ){

    if ( mkdir(path,S_IRWXU) != 0 ){
      printf("Error %d: %s\n"						\
	     "Unable to create configuration folder \"%s\".\n",errno, strerror(errno),path);
      exit(errno);
    }

  }

  /* The configuration filename is then concatanated.*/
  strcat(path,"reminder.conf");

  /* If the file does not exist, it is created.*/
  if (access(path, F_OK)){

    if( ( test_fd = open(path, O_RDWR | O_CREAT | O_EXCL, S_IRUSR | S_IWUSR) == -1)){
      printf("Error %d: %s\n"						\
	     "Unable to access configuration file \"%s\", please check permissions.\n",errno, strerror(errno),path);
      exit(errno);
    }
    /* Upon succesful creation, the file descriptor is closed.*/
    else
      close(test_fd);
  }

  gtk_init(&argc,&argv);

  time_elapse = time_check(path);
  
  action_decider(time_elapse,path);

  alarm_daemon(time_elapse);

  ui_popup(&argc,argv,path);

  return 0;
}
```

---

### Post by dwhitney67 on 2009-04-07
Fix this statement to be:
```

  path = malloc( strlen(home_dir) + strlen("/.reminder_config_temp/reminder.conf") + 1 );

```
You do not need to specify the sizeof(char)... AFAIK, for the last 30+ years it has been 1... and probably will be for the next.

The extra byte (the + 1) is for the null-termination byte.  If you do not specify this, you run the risk of overruning your buffer, which by the way, I'm surprised you didn't after the strcat().

---

### Post by PmDematagoda on 2009-04-07
> **dwhitney67 said:**
> Fix this statement to be:
```

  path = malloc( strlen(home_dir) + strlen("/.reminder_config_temp/reminder.conf") + 1 );

```
You do not need to specify the sizeof(char)... AFAIK, for the last 30+ years it has been 1... and probably will be for the next.

The extra byte (the + 1) is for the null-termination byte.  If you do not specify this, you run the risk of overruning your buffer, which by the way, I'm surprised you didn't after the strcat().

Yeah, I've just been using the "sizeof()" thing for(what I hope is) good practice, is it?

And yeah, you are right about the null-termination byte, and it is quite strange that there was no overflow at all, anyway, I increased the malloc to include the null-termination byte.:)

---

