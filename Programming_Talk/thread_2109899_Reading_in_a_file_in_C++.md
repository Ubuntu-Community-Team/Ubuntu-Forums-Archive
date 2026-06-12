---
title: "Reading in a file in C++"
date: 2013-01-28
forum: Programming Talk
---

### Post by Amulon on 2013-01-28
I am trying to read in a file that is similar to this:

push 10
pop
push 20
push 30
pop
push 10
push 50
push 20
push 20
pop

I am trying to make it so if it says push then it uses the pushfunction to push 10. And when it says pop it will pop off the top of the stack. Etc... 

When you read in a file how do you make it read in the string, then use the integer?

```
	getline(cin, fileAddress);
	ifstream textFile (fileAddress);

	//Tests the file
	if (textFile.fail())
	{
		cout << "File was not found"<< endl;
		system("PAUSE");
		exit (1);
	}
	else
		cout << "\nFile opened successfully" << endl;
```

That is what I have to read in the code but I am just stuck on how to store it then use it.

Thanks for the help!

---

### Post by steeldriver on 2013-01-28
have a look here

[http://www.cplusplus.com/reference/istream/istream/operator%3E%3E/](http://www.cplusplus.com/reference/istream/istream/operator%3E%3E/)

---

### Post by Amulon on 2013-01-28
> **steeldriver said:**
> have a look here

[http://www.cplusplus.com/reference/istream/istream/operator%3E%3E/](http://www.cplusplus.com/reference/istream/istream/operator%3E%3E/)

So you are saying that with each line of file that I read I should do a line of code like:

```
data >> stringVariable >> intVariable
```

---

### Post by dwhitney67 on 2013-01-29
> **Amulon said:**
> So you are saying that with each line of file that I read I should do a line of code like:

```
data >> stringVariable >> intVariable
```

Yes, something like that.  Providing of course that 'data' is a non-blocking stream.

For example:
```

fstream file("data.txt", fstream::in);

if (file)
{
    while (!file.eof())
    {
        string data;

        getline(file, data);

        if (file)
        {
            istringstream iss(data);
            string op;
            int value;  

            iss >> op >> value;


            // ...
        }
    }
}

```

---

### Post by Amulon on 2013-02-02
So I have used your insights to pretty much finish the project. Everything is good until 1 spot. The file is like:

push 10
push 10
push 10
push 10
pop
push 2
push 2
push 2

And when it doesnt read any data (other than the string) on the pop line, then the whole things gets screwed up. What hints/tips do you have to get this fixed?

---

### Post by dwhitney67 on 2013-02-02
> **Amulon said:**
> So I have used your insights ...

Whose insights?  (Your own?)
> **Amulon said:**
> 
And when it doesnt read any data (other than the string) on the pop line, then the whole things gets screwed up. What hints/tips do you have to get this fixed?
"Screwed up", etc -- what do these mean??

Keep in mind, that sensible people reading this post are not here to complete your assignment.  Show us what you have thus far attempted.

---

### Post by Amulon on 2013-02-02
Uh... ? Why would I say that thanks for using my own insights? Of course I mean't the people who helped me.

I am not mad/frustrated in the slightest about what people have replied. I am not saying that the people who helped me screwed up, I am saying that there is another problem I have discovered with my own code and I need some help with this.

---

### Post by dwhitney67 on 2013-02-02
> **Amulon said:**
> ... I have discovered with my own code and I need some help with this.

It is the weekend; I do not have the luxury of depending on my crystal ball to get insight into the current state of your code.

Perhaps if you posted it (that is, the code), along with the problem you are experiencing, I, or someone else, may be able to help you.

---

### Post by Amulon on 2013-02-02
Man, stop complaining.

---

### Post by dwhitney67 on 2013-02-02
> **Amulon said:**
> Man, stop complaining.

You just sealed your fate.

---

### Post by cariboo on 2013-02-02
Thread closed, as there doesn't seem to be any answers forth coming.

---

