---
title: "linux open/read/write/close is faster than those in STD C library?"
date: 2016-02-15
forum: Programming Talk
---

### Post by DaviesX on 2016-02-15
Hello, I've experimented with copying files using the linux system call vs fopen/fread/fwrite/fclose. It appears that using system calls are much faster than with the C functions. Here is the code I used:
```

static void copy_file_sys_with_buf(const char* src_path, const char* dest_path, int n)
{
	struct timer timer;
	timer_start(&timer);
	int i;
	for (i = 0; i < n; i ++) {
		int fsrc = open(src_path, O_RDONLY);
		int fdest = open(dest_path, O_CREAT | O_WRONLY);
		if (fsrc == -1)
			perror(src_path), exit(1);
		if (fdest == -1)
			perror(dest_path), exit(1);
		while (1) {
			char buf[BUFSIZ];
			int ret = read(fsrc, buf, BUFSIZ);
			if (ret == -1)
				perror("read"), exit(1);
			else if (ret == 0)
				break;
			ret = write(fdest, buf, ret);
			if (ret == -1)
				perror("write"), exit(1);
		}
		close(fsrc);
		close(fdest);
	}
	timer_stop(&timer);
	printf("Finished copying. Time used: %s\n", timer_to_string(&timer));
}


static void copy_file_stdio_with_buf(const char* src_path, const char* dest_path, int n)
{
	struct timer timer;
	timer_start(&timer);
	int i;
	for (i = 0; i < n; i ++) {
		FILE* fsrc = fopen(src_path, "rb");
		FILE* fdest = fopen(dest_path, "wb");
		if (fsrc == NULL)
			perror(src_path), exit(1);
		if (fdest == NULL)
			perror(dest_path), exit(1);
		while (1) {
			char buf[BUFSIZ];
			int ret = fread(buf, 1, sizeof(buf), fsrc);
			if (ret == 0)
				break;
			ret = fwrite(buf, 1, ret, fdest);
			if (ret == 0)
				fprintf(stderr, "Failed to write to destination\n");
		}
		fclose(fsrc);
		fclose(fdest);
	}
	timer_stop(&timer);
	printf("Finished copying. Time used: %s\n", timer_to_string(&timer));
}

```

The results of copying /usr/share/dict/american-english-huge for 1000 times shows:
```

System call with buffering: Time used(in seconds): WallClock: 2.017085, SystemTime: 1.976000, UserTime: 0.044000
Stdio call with buffering: Time used(in seconds): WallClock: 85.787013, SystemTime: 12.848000, UserTime: 0.748000

```

I wonder what makes the difference between stdio and system call? Will I have to sacrifice performance with being able to cross platforms?

---

### Post by DaviesX on 2016-02-15
ops, I forget to add I compiled and ran the test under:
Linux 4.2.0-27-generic #32-Ubuntu SMP x86_64 GNU/Linux
with:
gcc (Ubuntu 5.2.1-22ubuntu2) 5.2.1 20151010
ldd (Ubuntu GLIBC 2.21-0ubuntu4) 2.21

---

