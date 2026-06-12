---
title: "Forking in C"
date: 2011-04-19
forum: Programming Talk
---

### Post by raac on 2011-04-19
Hello guys, I have a question consider this code

```

int i;
pid_t child;
for (i = 0; i < 7; i++){
   if((child =fork()) == -1){
      perror("Error");
   }
   if(child == 0){
      fprintf(stderr, "C is number one\n");
      return 0;
   }else{             /*parent code*/
      while (r_waitpid(-1, NULL, WNOHANG) > 0) ;  /* clean zombies */
   }

}

fprintf(stderr, "In conclusion C rocks!!\n");
return 0;       


```

My question is how can I guarantee that the string "In conclusion C rocks!!\n", will be that LAST ONE to be executed????

In other words I don't want something like this...
"C is number one\n"
"In conclusion C rocks!!\n"
"C is number one\n"


thanks

---

### Post by Arndt on 2011-04-19
> **raac said:**
> Hello guys, I have a question consider this code

```

int i;
pid_t child;
for (i = 0; i < 7; i++){
   if((child =fork()) == -1){
      perror("Error");
   }
   if(child == 0){
      fprintf(stderr, "C is number one\n");
      return 0;
   }else{             /*parent code*/
      while (r_waitpid(-1, NULL, WNOHANG) > 0) ;  /* clean zombies */
   }

}

fprintf(stderr, "In conclusion C rocks!!\n");
return 0;       


```

My question is how can I guarantee that the string "In conclusion C rocks!!\n", will be that LAST ONE to be executed????

In other words I don't want something like this...
"C is number one\n"
"In conclusion C rocks!!\n"
"C is number one\n"


thanks

Your waitpid logic seems a little strange to me. Can you put in ordinary words what the code should do?

What is r_waitpid, by the way? I only find waitpid in the man pages.

---

### Post by raac on 2011-04-19
```

pid_t r_waitpid(pid_t pid, int *stat_loc, int options) {
   pid_t retval;
   while (((retval = waitpid(pid, stat_loc, options)) == -1) &&
           (errno == EINTR)) ;
   return retval;
}

```

---

### Post by raac on 2011-04-19
Any ideas guys???

---

### Post by slavik on 2011-04-19
it has to do with buffering I believe ... try fflush(); after each print.

---

