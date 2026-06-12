---
title: "C++, cin from file, output to a file"
date: 2008-09-13
forum: Programming Talk
---

### Post by Sharpiedeluxe on 2008-09-13
Okay, so I'm writing this program, and basically I want to test it with a bunch of text files, and make sure that the output is valid. So, I've been using 

      $ a.out < test.file > test.output 2> test.error

this is correct right? However, when I compare files, it appears that test.file is completely blank with nothing inside, as if it wasn't even taking stdin at all. However, if I run the program, immediately it prompts for input. Any suggestions? the code generally looks like:

      while (!cin.eof())
      {
            cin >> user_data;
            cin >> user_data2;
      }

this is the only thing in the code that I would see a problem with :( Any help would be great. Thanks.

     edit: Just found out that I get this if I output to an error file "<stdin>:106: warning: no newline at end of file", unfortunately, if its complaining about line 106, that's right in the middle of some code, so adding more lines doesn't help.

---

### Post by bfhicks on 2008-09-13
I have a little trick you might like.

When first writing the program, I just want to compile & run, not worry about providing input. So, I add two lines to the top of my code.



```
[color=#BC7A00]#include <iostream>
#include <fstream>
#include <string>
[/color]
[color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

ifstream fin([color=#BA2121]"cube.txt"[/color]);
[color=#BC7A00]#define cin fin
[/color]
[color=#B00040]int[/color] main()
{
	string line;
	[color=#008000]**while**[/color] (getline(cin,line))
	{
		cout [color=#666666]<<[/color] line [color=#666666]<<[/color] endl;
	}
	
	[color=#008000]**return**[/color] [color=#666666]1[/color];
}

```

To run this, I'll do:
```
./test
```
Then, I can check the output as it prints out to verify it.

Now, I'm ready to script it to run with a bunch of files, then I'll comment out two lines:
```
[color=#BC7A00]#include <iostream>
#include <fstream>
#include <string>
[/color]
[color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

[color=#408080][i]//ifstream fin("cube.txt");
//#define cin fin
[/i][/color]
[color=#B00040]int[/color] main()
{
	string line;
	[color=#008000]**while**[/color] (getline(cin,line))
	{
		cout [color=#666666]<<[/color] line [color=#666666]<<[/color] endl;
	}
	
	[color=#008000]**return**[/color] [color=#666666]1[/color];
}

```
Run program: provide input and save the output.
```
./test < cube.txt > cube_out.txt
```

---

### Post by dribeas on 2008-09-13
> **Sharpiedeluxe said:**
> $ a.out < test.file > test.output 2> test.error

this is correct right? However, when I compare files, it appears that test.file is completely blank with nothing inside, as if it wasn't even taking stdin at all.

Just to make sure we are clean on redirections: when you redirect input _from_ a file, the file must have the contents before hand, they are read and passed to the program as if a user was just typing those same characters on the console.

```

$ cat > file.txt << EOF
This is a file
with three lines
and this is the third line.
EOF
$ cat < file.txt # uses file.txt as user input
This is a file
with three lines
and this is the third line.
$ cat < file.txt > file2.txt # creates file2.txt with the output above
$ cat file2.txt # checks the contents of newly created file2.txt
This is a file
with three lines
and this is the third line.

```

---

### Post by Sharpiedeluxe on 2008-09-13
Right, I made sure that the input files were correct (no newlines at the bottom), and that I could cat them to the terminal. However, I renamed all the files with different extensions. Previously, they were .file, and after naming them to .txt, they all worked with the program. :confused: Doesn't make too much sense to me unfortunately xD But thanks for all the help.

---

