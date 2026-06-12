---
title: "Problem with fgetspent (shadow.h) in C"
date: 2008-04-16
forum: Programming Talk
---

### Post by antagon on 2008-04-16
I'm currently working on a school assignment. For this assignment I'm working on a small application for changing your Ubuntu password. The application is basically finished outside of one bug which seems completely illogical to me.

At the start of the application I retrieve an entry from a shadow file using the fgetspent method in shadow.h. After I've changed the password in this entry I have to write it to the shadow file again. The methods provided in shadow.h only allow for adding entries to the shadow file and not overwriting or deleting them. 

To solve this problem I want to read all the entries from the shadow file one by one, compare then compare the username of each entry to the username of the entry with the changed password. If they match, the changed entry is written to a temp file. If not, the entry I just read is written to it. At the end, the shadow file is overwritten by the temp file.

Now for the problem:
The changed entry is stored in a variable called shadow_entry. Each entry that I read is stored in a variable called temp_entry. However, each time that I read an entry and put it in temp_entry, the content of shadow_entry changes to the content of temp_entry. I've checked the pointer values of both shadow_entry and temp_entry but they don't match.

Here's the code:

```
void retr_shadow_entry(struct spwd * shadow_entry) {
	FILE * shadow_file;
	struct spwd * temp_entry;
      
       //Retrieve the password file entry for the user, to safely obtain his username.
	struct passwd * passwd_entry = getpwuid(getuid());
	shadow_file = fopen(SHADOW_FILE, "r");
       //Iterate through the entries in the shadow file until the entry for the user is found.
	temp_entry = fgetspent(shadow_file);
	while(temp_entry != 0) {
		printf("%u\n", temp_entry);
		if(strcmp(temp_entry->sp_namp, passwd_entry->pw_name) == 0) {
                       //The entry for the user is found.
			*shadow_entry = *temp_entry;
			break;
		}
		temp_entry = fgetspent(shadow_file);
	}	
	fclose(shadow_file);	
}

int write_shadow_entry(struct spwd * shadow_entry) {
	char command[256];
	struct spwd * temp_entry;
	FILE * shadow_file = fopen(SHADOW_FILE, "r");;
	FILE * temp_file = fopen(TEMP_FILE, "w");;
	if(shadow_file == 0 || temp_file == 0) {
		return 0;
	}
       //Iterate through all the entries in the shadow file.
	printf("User: %s.\n", shadow_entry->sp_namp);
	temp_entry = fgetspent(shadow_file);	
	printf("User 2: %s.\n", shadow_entry->sp_namp);
	while(temp_entry != 0) {
		if(strcmp(temp_entry->sp_namp, shadow_entry->sp_namp) == 0) {		
	                //The entry that was changed has been found.
			putspent(shadow_entry, temp_file);					
		} else {
                        //An unchanged entry has been found.
			putspent(temp_entry, temp_file);
		}
		temp_entry = fgetspent(shadow_file);
	}
	fclose(temp_file);
	fclose(shadow_file)
       //overwrite SHADOW_FILE with TEMP_FILE.
	sprintf(command, "mv %s %s", TEMP_FILE, SHADOW_FILE);
	system(command);
	return 1;
}
```

In the second method you see that I call printf two times, each time I print the name in the shadow entry. Somehow, the second time I get a different name ('root', which is the name of the first entry in the shadow file) then the first time.

Is there anyone here that sees any mistakes in the code that could be the cause of the problem? If so, thanks :)

---

### Post by antagon on 2008-04-16
Just solved the problem. Since I copied the struct content from temp_entry to shadow_entry using the l ine *shadow_entry = *temp_entry the char * in shadow_entry where pointing to the same space as the char * in temp_entry.

When I called fgetspent again in the second function it wrote it's name/password char * to the same memory location. Because of this, the name and password in shadow_entry were overwritten as well.

I'm using strcpy now to copy the name and password from temp_entry to shadow_entry.

What I still don't get is why fgetspent would write to the exact same location again. Is there anyone here that could explain it?

---

### Post by WW on 2008-04-16
Take a look at the manpage: **man fgetspent**.  In particular,
> 
For the non-reentrant functions, the return value may point  to  static
area, and may be overwritten by subsequent calls to these functions.

There are reentrant versions of the functions which allow you to provide the pointer(s) to the storage area.  These are described in the same man page.

---

### Post by antagon on 2008-04-16
Thanks for that. I missed that part of the man page. 

I'm using the reentrant version now and the problems have been solved.

---

