---
title: "[SOLVED] C file handling, sscanf()"
date: 2008-03-20
forum: Programming Talk
---

### Post by nephritiri on 2008-03-20
hey guys...
im having some problems in reading strings from a file.

data from the file are the ff:
 -10 1.5 0

i was able to read them, convert and save them in variables and write those values on the screen using this code:

[HTML]
   sscanf( buff, " %f%f%f", &l1,&l2,&l3 )
	printf("%f ", l1);
	printf("%f ", l2);
	printf("%f\n", l3);						
[/HTML]

however, the '-' sign is somehow truncated during the file reading 
coz the output is:

10.000000 1.500000 0.000000

can someone help me?
thanks.

---

### Post by ruy_lopez on 2008-03-20
I can't reproduce your problem. This is what I get:

File:
-10 -1 10

Output:
-10.000000 -1.000000 10.000000

```

int main()
{
	FILE *fp;
	char buf[24];
	float f1, f2, f3;

	if ((fp = fopen("file", "r")) == NULL) {
		printf("fopen error:\n");
		return -1;
	}

	fread(buf, sizeof(char), 24, fp);

	sscanf(buf, " %f %f %f", &f1, &f2, &f3);
	printf("%f %f %f\n", f1, f2, f3);
}

```

---

### Post by nephritiri on 2008-03-20
hey yeah, it worked. jz some prob on my loop structure coz 1st string read is overwritten by the 1st string of the 2nd line. how can i not figure it out first. hehe. thanks anyway! 

File:
-10 1.5 0
 10 3.5 0

---

