---
title: "Does anything look wrong in this C function?"
date: 2010-01-07
forum: Programming Talk
---

### Post by Jekshadow on 2010-01-07
I wrote a simple C function to load two values out of a config file, and it always says that my config file could not be read.

Source (Consider it GPL'd):
```
void readConfig() {
	FILE *file;
	file = fopen(CONFIG_FILE, "r");
	
	if (!file) {
		error("Failed to open config file! Do you have one?\n");
	}
	
	fscanf(file, "Port: %d", &port);
	fscanf(file, "Address: %s", path);
	
	if (!port || !path) {
		printf("%d,%s", port, path);
		error("Failed to read config file!\n");
	}
	
	fclose(file);
}
```

The config file:
```
Port: 2000
Address: "/home/myname/py/c/something/socket"
```

EDIT:

Yes, I did initialize 'port' and 'path' as global variables in the beginning of the code.

```

int port;
char *path;

```

---

### Post by Can+~ on 2010-01-07
```
char *path;
```

There's no space allocated to store the actual content of a string in path, you'll need to use malloc and free, or set a static maximum size (subject to overflows too)

```
char path[MAXPATHSIZE];
```

Second, since:

```
if (!port || !path) {
```

path is a pointer (or an array if you make it static sized) then path will always be a direction distinct from zero.

> fscanf(file, "Port: %d", &port);

You're missing a newline:

```
fscanf(file, "Port: %d\n", &port);
```

Finally, this is a poor method for parsing a file (empty spaces can ruin the parse), you should be retrieving lines and using a tokenizer (strtok) for more effective parsing. (Or any higher level language with better string support)

---

### Post by Sockerdrickan on 2010-01-07
> **Jekshadow said:**
> Source (Consider it GPL'd):
```
void readConfig() {
    FILE *file;
    file = fopen(CONFIG_FILE, "r");
    
    if (!file) {
        error("Failed to open config file! Do you have one?\n");
    }
    
    fscanf(file, "Port: %d", &port);
    fscanf(file, "Address: %s", path);
    
    if (!port || !path) {
        printf("%d,%s", port, path);
        error("Failed to read config file!\n");
    }
    
    fclose(file);
}
```
Applying a GPL license to 18 rows of C code is pointless

---

### Post by Jekshadow on 2010-01-07
> **Can+~ said:**
> ```
char *path;
```

There's no space allocated to store the actual content of a string in path, you'll need to use malloc and free, or set a static maximum size (subject to overflows too)

```
char path[MAXPATHSIZE];
```

Second, since:

```
if (!port || !path) {
```

path is a pointer (or an array if you make it static sized) then path will always be a direction distinct from zero.



You're missing a newline:

```
fscanf(file, "Port: %d\n", &port);
```

Finally, this is a poor method for parsing a file (empty spaces can ruin the parse), you should be retrieving lines and using a tokenizer (strtok) for more effective parsing. (Or any higher level language with better string support)

Thanks.

---

### Post by nvteighen on 2010-01-08
I don't get why port and path have to be globals; you could make your function take them as arguments without any hassle.

Also, your program will crash if the file actually doesn't exist. fclose() will be executed no matter if fopen() returns NULL... And calling fclose(NULL) is like free(NULL): Segfault.

---

