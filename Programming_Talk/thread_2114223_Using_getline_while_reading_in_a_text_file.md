---
title: "Using getline while reading in a text file"
date: 2013-02-09
forum: Programming Talk
---

### Post by sixstorm on 2013-02-09
Yet another issue I'm having with my Time Clock application written in C++.

Here is the case that I'm having issues with:

```
case 5:
			{
			string stuRemove;
			string tempA;

			cout << "Please enter the full name of the student you would like to remove (type 'quit' to exit): ";
			getline(cin, tempA);
			getline(cin, tempA);

			if (tempA=="quit") {
				break;
			}

			ifstream iFile("students.txt");
			if (!iFile) {
				cout << "ERROR: 'students.txt' not found!";
				break;
			}
			else {
				cout << "students.txt is now open" << endl;
			}

			ofstream oFile("temp.txt");
			if (!oFile) {
				cout << "ERROR: 'temp.txt' could not be created!";
				break;
			}
			else {
				cout << "temp.txt has been created" << endl;
			}
			
			for (int i=0; i<MAX_STUDENTS; i++) {
				getline(iFile, stuRemove);
				if (stuRemove!=tempA) {
					cout << "Student: " << stuRemove << endl;
					oFile << stuRemove << endl;
				}
				else {
					oFile << "ERROR" << endl;
					cout << "ERROR" << endl;
				}
			}

			iFile.close();
			oFile.close();
			remove("students.txt");
			rename("temp.txt", "students.txt");
		
			cout << "Press Any Key to Continue" << endl;
			cin.get();
			cin.get();
			break;
			}

```

The output creates "temp.txt" that is completely blank, which leads me to believe that it is not reading in the text file for some reason.  I'm also betting that the getline in the for loop is part of the problem, as it doesn't seem to read in the string.

Any clue why this doesn't work?

---

### Post by dwhitney67 on 2013-02-09
Why do you have two back-2-back calls to getline()?
```

	getline(cin, tempA);
        getline(cin, tempA);

```

What is it that you are trying to do?  Remove a particular entry from a file?

There are many ways to do this; the approach you are taking appears to be one of them.  You should consider stepping through your program using a debugger to see if the code is doing what you expect.

Btw, why the for-loop?  Shouldn't you be using a while-loop, possibly checking the state of the input stream (ifile) as you go along?

---

### Post by sixstorm on 2013-02-09
> **dwhitney67 said:**
> Why do you have two back-2-back calls to getline()?
```

	getline(cin, tempA);
        getline(cin, tempA);

```

What is it that you are trying to do?  Remove a particular entry from a file?

There are many ways to do this; the approach you are taking appears to be one of them.  You should consider stepping through your program using a debugger to see if the code is doing what you expect.

Btw, why the for-loop?  Shouldn't you be using a while-loop, possibly checking the state of the input stream (ifile) as you go along?

If you don't repeat the getline, it will "skip" and not let you input to tempA.

I've been using Geditor and G++ for all my coding, but I guess I'll download Codeblocks or Geany to run it through a debugger.

And yes, I agree that I should do a while loop.  I guess I was just testing it with a for loop for . . . well, testing.

---

### Post by dwhitney67 on 2013-02-09
> **sixstorm said:**
> If you don't repeat the getline, it will "skip" and not let you input to tempA.

Check your code; I bet you are reading some sort of input (from the user) prior to calling the aforementioned getline() functions.  When you read that input, you left a newline in the cin stream.

The rule of thumb is to use getline() to read all user input; never read input (even if all you require is a number) using cin directly.  If you require a number, or character or some other primitive data type, use getline(), and then convert to the appropriate type as needed.

> **sixstorm said:**
> 
I've been using Geditor and G++ for all my coding, but I guess I'll download Codeblocks or Geany to run it through a debugger.

Your system more than likely already has 'gdb' (which is the GNU Debugger).  You could also install 'ddd' which provides a graphical front-end to 'gdb'.

---

### Post by sixstorm on 2013-02-09
> **dwhitney67 said:**
> Check your code; I bet you are reading some sort of input (from the user) prior to calling the aforementioned getline() functions.  When you read that input, you left a newline in the cin stream.

The rule of thumb is to use getline() to read all user input; never read input (even if all you require is a number) using cin directly.  If you require a number, or character or some other primitive data type, use getline(), and then convert to the appropriate type as needed.


Your system more than likely already has 'gdb' (which is the GNU Debugger).  You could also install 'ddd' which provides a graphical front-end to 'gdb'.

Yes, the input is a person's name, such as "John Doe".  It should copy line by line to "temp.txt" and skip the line matching what the user input.  This is the only "way" that I've found to remove a line from a text file via Internet research.  Is there a better way?

I know that I could use sets or arrays to do the trick too.

---

### Post by sixstorm on 2013-02-10
I know I'm probably not taking the "right" way out on this, but I'm using a typical cin (asking user for first and last names separately) instead of getline.  It works well and I'll probably stick with it.  Thanks for your help guys!

---

