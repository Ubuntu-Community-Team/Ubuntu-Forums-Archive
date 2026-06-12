---
title: "syslog LOG_ERR LOG_INFO difference ?"
date: 2009-02-11
forum: Programming Talk
---

### Post by monkeyking on 2009-02-11
I'm trying to write my own daemon, but I'm having trouble seeing that distinguishes the syslog LOG_INFO and LOG_ERR.
When I tail /var/log/syslog and /var/log/daemon I get the same log messages.

thanks in advance

[PHP]
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>
#include <syslog.h>
#include <string.h>
#include <stdarg.h>
#include <unistd.h>


char *appname = NULL;

void log_init(){
  openlog(appname,LOG_PID,LOG_DAEMON);
}


void log_msg (const char *fmt, ...)     {
  char msg[1024];
  va_list args;

  va_start(args, fmt);
  vsnprintf(msg, sizeof(msg), fmt, args);
  va_end(args);
  syslog(LOG_INFO, "%.500s", msg);
}


void log_err (const char *fmt, ...)     {
  char msg[1024];
  va_list args;

  va_start(args, fmt);
  vsnprintf(msg, sizeof(msg), fmt, args);
  va_end(args);
  syslog(LOG_ERR, "%.500s", msg);
}


static void sigterm_handler (int sig)   {
  printf("%s:SIGTERM signal received \n",appname);
  log_msg("%s: SIGTERM received\n");
  closelog();
  exit(0);
}

int main(int argc, char *argv[]){
  int var;
  if(fork())//fork of parent                                                                   
    _exit(0);

  signal(SIGTERM, (void *) &sigterm_handler);

  if(strchr(argv[0],'/'))
    appname = strrchr(argv[0], '/')+1;
  else
    appname = argv[0];

  log_init();

  log_msg("MSG");
  log_err("ERR");

  while(1){


  }

  return 0;
}




[/PHP]

---

