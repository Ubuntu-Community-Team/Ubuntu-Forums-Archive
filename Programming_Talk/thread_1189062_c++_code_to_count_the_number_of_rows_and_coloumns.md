---
title: "c++ code to count the number of rows and coloumns"
date: 2009-06-16
forum: Programming Talk
---

### Post by prabhanjan2906 on 2009-06-16
i needed a c++ code to display row and column of any given matrix. the matrix being present in a text file. the objective is to read the matrix from a file and to display the number of rows and columns.

---

### Post by Bachstelze on 2009-06-16
This sounds very much like a school assignment. Anyway, moved to Programming Talk.

---

### Post by prabhanjan2906 on 2009-06-16
actually i need to do the same for 2 matrices ad add them..

---

### Post by Zugzwang on 2009-06-16
Convince us that this is not homework. Posting homework questions is against the rules of this forum.

---

### Post by Mirge on 2009-06-16
Show us what you've done so far... so we know where you need help.

---

### Post by prabhanjan2906 on 2009-06-16
#include<iostream.h>
#include<ctype.h>
#include<fstream.h>
#include<conio.h>
void main()
{
	fstream fptr("kk.txt",ios::in|ios::out);
	char ch;
	int n=0,m=1,row,col;
	clrscr();
	fptr.seekg(0,ios::beg);
	while(!fptr.eof())
	{
		fptr.get(ch);
		if(ch!='\n')
		{
			if(isdigit(ch))
			{       n=n+1;
				if(!fptr.eof())
				{
					cout<<ch;

				}
			}

		 }
		 if(ch=='\n')
		 m=m+1;
	 }
	 row=m;
	 col=n/m;

	fptr.clear();
	cout<<endl<<row<<"  "<<col;
	}

this will consider only a single digit number. but for a 2 or more digit number it does not work properly

---

### Post by kjohansen on 2009-06-16
unless you have delimiters in the text file you cant do it.  How do I know if 101010 is 1,0,1,0,1,0, or 10,10,10 or 101,010, or  you get the point.  You will need to store the file with commas or spaces or some sort of delimiter...

---

### Post by Mirge on 2009-06-16
> **prabhanjan2906 said:**
> #include<iostream.h>
#include<ctype.h>
#include<fstream.h>
#include<conio.h>
void main()
{
    fstream fptr("kk.txt",ios::in|ios::out);
    char ch;
    int n=0,m=1,row,col;
    clrscr();
    fptr.seekg(0,ios::beg);
    while(!fptr.eof())
    {
        fptr.get(ch);
        if(ch!='\n')
        {
            if(isdigit(ch))
            {       n=n+1;
                if(!fptr.eof())
                {
                    cout<<ch;

                }
            }

         }
         if(ch=='\n')
         m=m+1;
     }
     row=m;
     col=n/m;

    fptr.clear();
    cout<<endl<<row<<"  "<<col;
    }

this will consider only a single digit number. but for a 2 or more digit number it does not work properly

Please enclose your source code in [ code ]..[ /code ] tags. (no spaces).

```

#include<ctype.h>
#include<fstream.h>
#include<conio.h>
void main()
{
    fstream fptr("kk.txt",ios::in|ios::out);
    char ch;
    int n=0,m=1,row,col;
    clrscr();
    fptr.seekg(0,ios::beg);
    while(!fptr.eof())
    {
        fptr.get(ch);
        if(ch!='\n')
        {
            if(isdigit(ch))
            {       n=n+1;
                if(!fptr.eof())
                {
                    cout<<ch;

                }
            }

         }
         if(ch=='\n')
         m=m+1;
     }
     row=m;
     col=n/m;

    fptr.clear();
    cout<<endl<<row<<"  "<<col;
    }

```

---

### Post by dwhitney67 on 2009-06-16
Say, two numbers separated by a white-space:
```

#include <fstream>
#include <iostream>

int main()
{
  using namespace std;

  fstream file("kk.txt", ios::in);

  int row = 0;
  int col = 0;

  file >> row >> col;

  cout << "row = " << row << ", col = " << col << endl;
}

```
It doesn't get any easier than this.

---

### Post by MadCow108 on 2009-06-16
or for arbitrary seperation:
```

#include <sstream>
string line;
	while (std::getline(filestream,line))
	{
		stringstream s(line);
		std::cout << "newline" << std::endl;
		string token;
		while (std::getline(s,token,'-'))
		{
			std::cout << "token: "<< token << std::endl;
		}
	}

```

also drop the .h in the #includes.
c++ standard headers are included without the ending

---

