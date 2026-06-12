---
title: "Wtf c++"
date: 2011-06-14
forum: Programming Talk
---

### Post by conradin on 2011-06-14
A subordinate of mine wrote a program last year, we later fired him for insubordination. I just found one of the programs he wrote and claimed to 
serve the function of converting json files to another format of text files. So Im looking at the code, and I cant see anything usefull about it. 
Then again its been 2-3 years since I have given C++ any thought at all.
Skilled Forums Users, I beseech thee: What is this Garbage??

```

#include <iostream>

#include <dirent.h>

#include <fstream>

#include <iomanip>



using namespace std;



int main()

{

	DIR *dp;

	struct dirent *dirp;

	char ch;



	dp = opendir(".");



	while(((dirp = readdir(dp)) !=NULL))

	{

		

		cout << "\n" << left << setw(30) << dirp->d_name << "Number : " << dirp->d_type;	

	}

	closedir(dp);

	cout << endl;

	cin >> ch;

	return 0;

}


```

---

### Post by lisati on 2011-06-14
Without actually trying it, it looks like some kind of simple directory listing program to me.

---

### Post by conradin on 2011-06-14
I dont remember what the guy was working on, but I Know it was supposed to do some conversion. I just compiled it and ran it, I see no evidence of any conversions, but it does list the directories.

---

### Post by psusi on 2011-06-14
Yea, all that does is list the files in the current directory.

---

### Post by conradin on 2011-06-14
I already knew that guy was full of BS, This is just more proof. For me its hilarious.

---

### Post by CptPicard on 2011-06-15
You were his manager and need to ask help to read that piece of code? ;)

---

### Post by Tony Flury on 2011-06-15
> **CptPicard said:**
> You were his manager and need to ask help to read that piece of code? ;)

In most industries management is based at least in part on trusting your subordinate team members to be experts in their areas, while you manage the work flow into the team and the issues around scheduling, finance etc. It is clear in this case that the guy was not up to the job, but it would not be uncommon for a manager to not be able to do some of the skilled jobs that members of their team do.
I am currently a manager of a very diverse team - i could not do most of the jobs that my team do, but i do ask for proof that it is complete - e.g. test reports etc.

---

### Post by CptPicard on 2011-06-15
> **Tony Flury said:**
> In most industries management is based at least in part on trusting your subordinate team members to be experts in their areas, while you manage the work flow into the team and the issues around scheduling, finance etc.

True, but at least in the SW field typically I wouldn't like seeing a managerial type that operates close to actual production who hasn't been a programmer himself.

I'm surprised this piece of nonfunctional code wasn't caught earlier, it's so blatant... :)

---

### Post by TwoEars on 2011-06-15
> **CptPicard said:**
> True, but at least in the SW field typically I wouldn't like seeing a managerial type that operates close to actual production who hasn't been a programmer himself.

I'm surprised this piece of nonfunctional code wasn't caught earlier, it's so blatant... :)

Indeed. You would've thought it would've come up in a code review.

---

