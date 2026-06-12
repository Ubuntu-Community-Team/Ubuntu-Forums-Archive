---
title: "Help with C"
date: 2012-05-07
forum: Programming Talk
---

### Post by faresallayl on 2012-05-07
Hi everybody i'm trying to make that work:
ssize_t len;
	printf("message à envoyer: \n");
	fflush(stdout);

	if (fgets(buff, BUF_SIZE, stdin) == NULL) {
	fprintf(stderr, "Echec de lecture des données reçus\n");
	exit(EXIT_FAILURE);
	}

	len = write(s, buff, strlen(buff));

	if(strcmp(buff,"quitter")==0)
exit(0);

there is a problem in 
if(strcmp(buff,"quitter")==0)
exit(0);
it's not working

---

### Post by 11jmb on 2012-05-07
what error messages are you getting? at compile-time or runtime?

also, I'm assuming this is a chunk of your main(), right? Please post the entire function. Of particular interest to me is where "buff" is declared.

---

### Post by Bachstelze on 2012-05-08
> **faresallayl said:**
> 
there is a problem in 
if(strcmp(buff,"quitter")==0)
exit(0);
it's not working

The newline.

---

