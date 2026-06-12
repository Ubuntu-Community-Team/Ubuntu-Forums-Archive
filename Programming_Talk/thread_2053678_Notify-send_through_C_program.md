---
title: "Notify-send through C program"
date: 2012-09-05
forum: Programming Talk
---

### Post by hackintoshrao on 2012-09-05
[COLOR=Red]#include<unistd.h>
int main()
{
    char buffer[]="GOOD!!MORNING!!";
    system("notify-send buffer");
    return 0;
}[/COLOR]

I want to send the string stored at **buffer[]** as argument to** notify-send** through the **system()** function call [COLOR=Black], so that i would get the content of string buffer as desktop notification . How to solve this problem ???[/COLOR]

---

### Post by Hadaka on 2012-09-05
Hi, you could use crontab with a script to run at a specified time and e-mail
notification activated. While a  message would not be delivered to the desktop,
it would light up your e-mail notification envelope...top right. and that would
have your greeting or message.

---

### Post by oldos2er on 2012-09-05
Moved to Programming Talk.

---

### Post by Odexios on 2012-09-06
> **hackintoshrao said:**
> [COLOR=Red]#include<unistd.h>
int main()
{
    char buffer[]="GOOD!!MORNING!!";
    system("notify-send buffer");
    return 0;
}[/COLOR]

I want to send the string stored at **buffer[]** as argument to** notify-send** through the **system()** function call [COLOR=Black], so that i would get the content of string buffer as desktop notification . How to solve this problem ???[/COLOR]system might not be the best function to use, but you can do it easily; something like this:

[php]

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define SNOTIFY "notify-send"
int main(int argc, char *argv[])
{
    char buffer[]="Whatever";
    char *system_call;
    int dim_arg;
    int dim_snotify;
    int dim_system_call;

    dim_arg = strlen(buffer);
    dim_snotify = strlen(SNOTIFY);
    dim_system_call = dim_snotify + 1 + dim_arg + 1;
    system_call=malloc(sizeof(char) * dim_system_call);

    sprintf(system_call, "%s %s", SNOTIFY, buffer);
    system(system_call);

    return 0;

}[/php]

There's no error checking or anything, of course.

---

