---
title: "more strings"
date: 2007-02-12
forum: Programming Talk
---

### Post by band-aid on 2007-02-12
Some of you may remember my post that I made over the weekend asking for my help splitting a string. I have decided that my problem is that I was trying to use apstring.h which is not standard and therefore not widely supported. I have essentially scrapped my old program and am starting anew using string and vector and I think its going better. I have a few questions though.

1. Is it possible to store a string into a vector with the first word in the first cell (I forget what their called e.g. vector[1]) and the rest of the string in the next cell?

2. what is the easiest way to split a std::string into two separate strings at the first space. I was thinking about finding the location of the first space (lets say we're looking in string A), copying the text from the beginning of the string to a different string (lets call this one string B), then copying the text from the space to the end of the string into another string (lets call this one string C). This process seems really inefficient and I'm not even sure how to pull it off. Any help is appreciated.

---

### Post by g3k0 on 2007-02-12
1. Yes
2. You can do 
position = foo.find(" ",0);  //find the first space starting at position 0 
  to find the first place

then use foo.substr(0,position)

I wrote the program ill try to hide the answer by putting lots of garbage in the beginning

Note: I did not put any checks in place for this.  It will not work correctly if say you dont have a space
```

//Scroll down to see how I did it



































#include <iostream>
#include <vector>
#include <string>
using namespace std;

int main(){
	vector<string> myVector;
	int position = 0;
	string foo;
	
	getline(cin,foo);  //Get the entire input
	position = foo.find(" ",0);  //find the first space starting at position 0
	
	myVector.push_back(foo.substr(0,position));  //Parse the first word
	myVector.push_back(foo.substr(position+1,foo.length()));
	
	cout <<endl<<myVector[0]<<endl<<myVector[1]<<endl;
	return 0;
}
```

---

### Post by band-aid on 2007-02-12
Wow that makes perfect sense. Thanks a ton!

but now I have another question.

I need to take the second part of the vector (myVector[1]) in your example and copy it into a different cell in another vector (time for ASCII art)


```

myVector [TheFirstWord][TheRestOfIt]

theOtherVector [nothing][nothing][TEXT][nothing][nothing]

```

I need to be able to take TheRestOfIt out of myVector and store it in the second cell in theOtherVector while keeping the rest of the cells in the same place. 

Once again, thanks a lot.

---

### Post by g3k0 on 2007-02-12
You could use the insert command for a vector assuming the position is available
It puts something in the position and then pushes everything else to the right of it.

If there is a a blank string in that position and you just want to set it you could do theOtherVector[1] = myVector[1] i believe.  I use insert in the adjusted example code below.

```

#include <iostream>
#include <vector>
#include <string>
using namespace std;

int main(){
	vector<string> myVector;
	vector<string> theOtherVector;
	int position = 0;
	string foo;
	
	getline(cin,foo);  //Get the entire input
	position = foo.find(" ",0);  //find the first space starting at position 0
	
	myVector.push_back(foo.substr(0,position));  //Parse the first word
	myVector.push_back(foo.substr(position+1,foo.length()));
	
	//cout <<endl<<myVector[0]<<endl<<myVector[1]<<endl;  //commend out to avoid confusion
	theOtherVector.push_back("hah");   //fill the vector with meaningless garbage to illustrate how insert works
	theOtherVector.push_back("hah1");
	theOtherVector.push_back("hah2");
	theOtherVector.push_back("hah3");
	
	theOtherVector.insert(theOtherVector.begin()+1,myVector[1]);  
	cout << theOtherVector[0] << endl << theOtherVector[1] << endl << theOtherVector[2] << endl ;
	
	
	return 0;
}

```

---

### Post by band-aid on 2007-02-12
ok, you guys have been REALLY helpful. I've made more progress today than I did in hours over the weekend. I am having one error when compiling, I'll paste in a code snippet and explain what I am trying to accomplish.

```

  if(temp[0] = operations[0]){
                       above = temp[1];
                       }

```

What this code is supposed to do is look at the first cell of temp and compare it to the first cell of operations. operations looks like this.

```

vector<string>operations(7); //This contains the operations to compare to later, they are in this order above,below,left,right,sandwich,bookend,end

```

It is checking to see if temp[0] (the first word of the string the user inputted, the command) is equal to above (operations[0], and if it is store the contents of temp[1] into the string above for printing in the proper location later. I have repeated this exercise 7 times in my code in a sort of block of if's and else if's. I get the same error for each one. It is the first line in the snippet I pasted. The error reads

```

50 C:\Dev-Cpp\projects\yetanotherreattempt.cpp could not convert `(+(&temp)->std::vector<_Tp, _Alloc>::operator[] [with _Tp = std::string, _Alloc = std::allocator<std::string>](0u))->std::basic_string<_CharT, _Traits, _Alloc>::operator= [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>](((const std::basic_string<char, std::char_traits<char>, std::allocator<char> >&)((const std::basic_string<char, std::char_traits<char>, std::allocator<char> >*)(+(&operations)->std::vector<_Tp, _Alloc>::operator[] [with _Tp = std::string, _Alloc = std::allocator<std::string>](0u)))))' to `bool' 

```

Thanks for all the help.

---

### Post by g3k0 on 2007-02-12
Right off the bat there is a problem with your if statement.

You are doing  if(temp[0] = operations[0]){
a condition uses == to compare things
= is used to assign

---

### Post by band-aid on 2007-02-13
Ok that was a stupid mistake. I fixed it and it compiled correctly but runs wrong. I need to input 3 lines, then start taking the input and splitting reading the first word as a command and storing rest in the correct location determined by the command. Then it must print out the strings with the extra stuff attached. Here is my code.

```

#include <string>
#include <vector>
#include <iostream>

using namespace std;

int main(){
    cout <<"This program will accept three lines of text and then switch to a command mode. In command mode you may enter a command (above,below,right,left,bookend,sandwich) and a line of text to be applied as a decoration.\n";
    
    
    vector<string>lineone(5);
    vector<string>linetwo(5);
    vector<string>linethree(5);
    string above;
    string below;
    string sandwich;
    
    cout << "you may enter your lines now\n";
    cin >> lineone[2];
    cin >> linetwo[2];
    cin >> linethree[2];
    
    int cut = 0;
    string input;
    vector<string>temp;
    int breakpoint = 0;
    while(cut != 1){
    vector<string>operations(7); //This contains the operations to compare to later, they are in this order above,below,left,right,sandwich,bookend,end
    
    operations.push_back("above");
    operations.push_back("below");
    operations.push_back("left");
    operations.push_back("right");
    operations.push_back("sandwich");
    operations.push_back("bookend");
    operations.push_back("end");
    
      getline(cin,input);
      breakpoint = input.find(" ",0);
      
      temp.push_back(input.substr(0,breakpoint));       
      temp.push_back(input.substr(breakpoint+1,input.length()));
            
            
            
            if(temp[0] == operations[0]){
                       above = temp[1];
                       }
                       else if(temp[0] == operations[1]){
                                  below = temp[1];
                                  }
                                  else if(temp[0] == operations[2]){
                                             lineone[1] = temp[1];
                                             linetwo[1] = temp[1];
                                             linethree[1] = temp[1];
                                             }
                                             else if(temp[1] == operations[3]){
                                                  lineone[3] = temp[1];
                                                  linetwo[3] = temp[1];
                                                  linethree[3] = temp[1];
                                                  }
                                                  else if(temp[1] == operations[4]){
                                                       lineone[0] = temp[1];
                                                       linetwo[0] = temp[1];
                                                       linethree[0] = temp[1];
                                                       lineone[4] = temp[1];
                                                       linetwo[4] = temp[1];
                                                       linetwo[4] = temp[1];
                                                       }
                                                       else if(temp[0] == operations[5]){
                                                            sandwich = temp[1];
                                                            }
                                                            else if(temp[0] == operations[6]){
                                                                 cut = 1;
                                                                 }
                                                                 
            cout << sandwich;
            cout << above;
            cout << lineone[0] << lineone[1] << lineone[2] << lineone[3] << lineone[4];
            cout << linetwo[0] << linetwo[1] << linetwo[2] << linetwo[3] << lineone[4];
            cout << linethree[0] << linethree[1] << linetwo[2] << linetwo[3] << linetwo[4];
            cout << below;
            cout << sandwich;
            
            return 0;
}}

```

thanks for the help

---

### Post by g3k0 on 2007-02-13
Well a few notable things are -

Your while loop should not have return 0 in it
Your output at the end goes linetwo[0] << linetwo[1] << line**one**[2] .  It does this with a bunch of things
You are not erasing the contents of temp each time.  You are pushing on to it over and over so your compares wont work.  Look at the size grow.

I'll see if I can find more later

---

### Post by g3k0 on 2007-02-13
All the operations pushes should be outside the loop.. you are  adding them on each time you go through just like u are doing with the temp.

Your 5th if down in the else if structure makes the mistake with linetwo[4] line**three**[4]

Some reason your getline isnt working the first time around... ill see if I can figure out why

---

### Post by band-aid on 2007-02-13
Ok, I've moved my operations outside the while loop. I haven't the slightest why I put them there in the first place. I must not have been playing attention. I was writing that while watching 24 lol. I'll keep messing with it and see if I can get it sorted out. please post back if you get it working correctly. You guys have been a tremendous help. Thanks.

Band-aid

EDIT: For some reason it is bypassing cin >> linethree[2]

When I tell my debugger to run it to the while loop it takes the first two lines then flys through to the loop without even registering that statement.

---

### Post by g3k0 on 2007-02-13
Ok i know whats happening.  The first getline doesnt work because it is being used after cin.
cin does not pick up the last linefeed (aka \n). Getline picks it up thinking you typed it in.  do a 
cin.ignore(100,'\n'); sometime before the loop.  Do this and the other fixes I mentioned and you should be good.  Any other problems will just because you are not telling the compiler what u want correctly.  Im not sure what its supposed to do so I cannot fix these errors (if there are any).

---

### Post by band-aid on 2007-02-13
It compiles fine but is acting kinda funny. It allows me to enter three lines but instead of going into the command mode type thing it prints the first line then either the second one in the first line twice or the second line twice. Lemme give some examples

```

INPUT:
lineone
linetwo
linethree
above %%%

OUTPUT:
lineonelinetwolinethree


INPUT:
line one
line two
line three

OUTPUT:
lineoneone


```

The problem this program is supposed to solve is this. Allow the user to input three lines of text. Then accept the commands above,below,left,right,sandwich,bookend. After these commands (in the same line, separated by a space) the user will enter a "decoration" which will be applied to the lines of text. The way it is supposed to work is this.

```


INPUT:
This is the first line of text.
This is the second line of text.
This is the third line of text.
above %%%%%%%%
below &&&&&&&&
left !!!!!!!!
right ********
sandwich ^^^^^^^^^^
bookend ()

OUTPUT:
^^^^^^^^^^
()!!!!!!!!This is the first line of text.********()
()!!!!!!!!This is the second line of text.********()
()!!!!!!!!This is the third line of text.********()
^^^^^^^^^^


```

I'll keep at it. Thanks for the help.

EDIT: after a bit more work I don't think it is executing the while loop.

---

### Post by g3k0 on 2007-02-13
Can you give me your latest code?

---

### Post by band-aid on 2007-02-13
```


#include <string>
#include <vector>
#include <iostream>

using namespace std;

int main(){
    cout <<"This program will accept three lines of text and then switch to a command mode. In command mode you may enter a command (above,below,right,left,bookend,sandwich) and a line of text to be applied as a decoration.\n";
    
    
    vector<string>lineone(5);
    vector<string>linetwo(5);
    vector<string>linethree(5);
    string above;
    string below;
    string sandwich;
    
    cout << "you may enter your lines now\n";
    cin >> lineone[2];
    cin >> linetwo[2];
    cin >> linethree[2];
    
    cin.ignore(100,'\n');
    
    int cut = 1;
    string input;
    vector<string>temp;
    int breakpoint = 0;
    
    vector<string>operations(7); //This contains the operations to compare to later, they are in this order above,below,left,right,sandwich,bookend,end
    
    operations.push_back("above");
    operations.push_back("below");
    operations.push_back("left");
    operations.push_back("right");
    operations.push_back("sandwich");
    operations.push_back("bookend");
    operations.push_back("end");
    
    
    while(cut == 1){
    
   
    
      getline(cin,input);
      breakpoint = input.find(" ",0);
      
      temp.push_back(input.substr(0,breakpoint));       
      temp.push_back(input.substr(breakpoint+1,input.length()));
            
            
            
            if(temp[0] == operations[0]){
                       above = temp[1];
                       }
                       else if(temp[0] == operations[1]){
                                  below = temp[1];
                                  }
                                  else if(temp[0] == operations[2]){
                                             lineone[1] = temp[1];
                                             linetwo[1] = temp[1];
                                             linethree[1] = temp[1];
                                             }
                                             else if(temp[1] == operations[3]){
                                                  lineone[3] = temp[1];
                                                  linetwo[3] = temp[1];
                                                  linethree[3] = temp[1];
                                                  }
                                                  else if(temp[1] == operations[4]){
                                                       lineone[0] = temp[1];
                                                       linetwo[0] = temp[1];
                                                       linethree[0] = temp[1];
                                                       lineone[4] = temp[1];
                                                       linetwo[4] = temp[1];
                                                       linethree[4] = temp[1];
                                                       }
                                                       else if(temp[0] == operations[5]){
                                                            sandwich = temp[1];
                                                            }
                                                            else if(temp[0] == operations[6]){
                                                                 cut = 0;
                                                                 }
                                                                 
            cout << sandwich;
            cout << above;
            cout << lineone[0] << lineone[1] << lineone[2] << lineone[3] << lineone[4];
            cout << linetwo[0] << linetwo[1] << linetwo[2] << linetwo[3] << lineone[4];
            cout << linethree[0] << linethree[1] << linetwo[2] << linetwo[3] << linetwo[4];
            cout << below;
            cout << sandwich;
            
            return 0;
}}


```

I made the fixes you suggested and have toyed around with it a bit.

---

### Post by g3k0 on 2007-02-13
You have not done all the fixes I posted.
I notice the while and the output fixes I did are still not in.  Read my last couple posts (post 8 in particular)

---

### Post by band-aid on 2007-02-13
Ok I think I have everything fixed. I also noticed that I was pushing my strings into my operations vector in the wrong direction. Now when it runs it is going though the while loop but does not quit out of it when I issue the line "end" as I specified in my last else if. Anyway, here it is.

```


#include <string>
#include <vector>
#include <iostream>

using namespace std;

int main(){
    cout <<"This program will accept three lines of text and then switch to a command mode. In command mode you may enter a command (above,below,right,left,bookend,sandwich) and a line of text to be applied as a decoration.\n";
    
    
    vector<string>lineone(5);
    vector<string>linetwo(5);
    vector<string>linethree(5);
    string above;
    string below;
    string sandwich;
    
    cout << "you may enter your lines now\n";
    cin >> lineone[2];
    cin >> linetwo[2];
    cin >> linethree[2];
    
    cin.ignore(100,'\n');
    
    int cut = 1;
    string input;
    vector<string>temp;
    int breakpoint = 0;
    
    vector<string>operations(7); //This contains the operations to compare to later, they are in this order above,below,left,right,sandwich,bookend,end
    
    operations.push_back("end");
    operations.push_back("bookend");
    operations.push_back("sandwich");
    operations.push_back("right");
    operations.push_back("left");
    operations.push_back("below");
    operations.push_back("above");
    
    
    while(cut == 1){
    
   
    
      getline(cin,input);
      
      
      breakpoint = input.find(" ",0);
      temp.clear();
      temp.push_back(input.substr(0,breakpoint));       
      temp.push_back(input.substr(breakpoint+1,input.length()));
            
            
            
            if(temp[0] == operations[0]){
                       above = temp[1];
                       }
                       else if(temp[0] == operations[1]){
                                  below = temp[1];
                                  }
                                  else if(temp[0] == operations[2]){
                                             lineone[1] = temp[1];
                                             linetwo[1] = temp[1];
                                             linethree[1] = temp[1];
                                             }
                                             else if(temp[0] == operations[3]){
                                                  lineone[3] = temp[1];
                                                  linetwo[3] = temp[1];
                                                  linethree[3] = temp[1];
                                                  }
                                                  else if(temp[0] == operations[4]){
                                                       lineone[0] = temp[1];
                                                       linetwo[0] = temp[1];
                                                       linethree[0] = temp[1];
                                                       lineone[4] = temp[1];
                                                       linetwo[4] = temp[1];
                                                       linethree[4] = temp[1];
                                                       }
                                                       else if(temp[0] == operations[5]){
                                                            sandwich = temp[1];
                                                            }
                                                            else if(temp[0] == operations[6]){
                                                                 cut = 0;
                                                                 
                                                                 }
                                                                 }
            cout << sandwich;
            cout << above;
            cout << lineone[0] << lineone[1] << lineone[2] << lineone[3] << lineone[4];
            cout << linetwo[0] << linetwo[1] << linetwo[2] << linetwo[3] << linetwo[4];
            cout << linethree[0] << linethree[1] << linethree[2] << linethree[3] << linethree[4];
            cout << below;
            cout << sandwich;
            
            return 0;
}


```

---

### Post by g3k0 on 2007-02-13
You were correct in the order of operations the first time, push_back sticks each one on the back of the vector.  When u declare operations u shouldnt have (7) there since u are doing pushback the first one is starting at position 8 rather then filling in 1.

---

### Post by band-aid on 2007-02-13
ok I fixed the order by which my operations were put into the vector. Removed the (7) like you said, and added some endline characters in my output block which I realized I needed after some toying with it. Now it works perfectly whenever the first three lines that the user enters (the ones the decorations are to be attached to) are only one word. It seems to have problems with input with spaces. Theres probably something wrong with the way I let the user insert data into the vector (cin >> lineone[2]). I may try to have the users input put in a string then insert that into the vector using some vector function. Heres my code now.

```

#include <string>
#include <vector>
#include <iostream>

using namespace std;

int main(){
    cout <<"This program will accept three lines of text and then switch to a command mode. In command mode you may enter a command (above,below,right,left,bookend,sandwich) and a line of text to be applied as a decoration.\n";
    
    
    vector<string>lineone(5);
    vector<string>linetwo(5);
    vector<string>linethree(5);
    string above;
    string below;
    string sandwich;
    
    cout << "you may enter your lines now\n";
    cin >> lineone[2];
    cin >> linetwo[2];
    cin >> linethree[2];
    
    cin.ignore(100,'\n');
    
    int cut = 1;
    string input;
    vector<string>temp;
    int breakpoint = 0;
    
    vector<string>operations; //This contains the operations to compare to later, they are in this order above,below,left,right,sandwich,bookend,end
    
    operations.push_back("above");
    operations.push_back("below");
    operations.push_back("left");
    operations.push_back("right");
    operations.push_back("sandwich");
    operations.push_back("bookend");
    operations.push_back("end");
    
    
    while(cut == 1){
    
   
    
      getline(cin,input);
      
      
      breakpoint = input.find(" ",0);
      temp.clear();
      temp.push_back(input.substr(0,breakpoint));       
      temp.push_back(input.substr(breakpoint+1,input.length()));
            
            
            
            if(temp[0] == operations[0]){
                       above = temp[1];
                       }
                       else if(temp[0] == operations[1]){
                                  below = temp[1];
                                  }
                                  else if(temp[0] == operations[2]){
                                             lineone[1] = temp[1];
                                             linetwo[1] = temp[1];
                                             linethree[1] = temp[1];
                                             }
                                             else if(temp[0] == operations[3]){
                                                  lineone[3] = temp[1];
                                                  linetwo[3] = temp[1];
                                                  linethree[3] = temp[1];
                                                  }
                                                  else if(temp[0] == operations[5]){
                                                       lineone[0] = temp[1];
                                                       linetwo[0] = temp[1];
                                                       linethree[0] = temp[1];
                                                       lineone[4] = temp[1];
                                                       linetwo[4] = temp[1];
                                                       linethree[4] = temp[1];
                                                       }
                                                       else if(temp[0] == operations[4]){
                                                            sandwich = temp[1];
                                                            }
                                                            else if(temp[0] == operations[6]){
                                                                 cut = 0;
                                                                 
                                                                 }
                                                                 }
            cout << sandwich << "\n";
            cout << above << "\n";
            cout << lineone[0] << lineone[1] << lineone[2] << lineone[3] << lineone[4] << "\n";
            cout << linetwo[0] << linetwo[1] << linetwo[2] << linetwo[3] << linetwo[4] << "\n";
            cout << linethree[0] << linethree[1] << linethree[2] << linethree[3] << linethree[4] << "\n";
            cout << below << "\n";
            cout << sandwich << "\n";
            
            return 0;
}

```

thanks again for the help

---

### Post by g3k0 on 2007-02-13
The reason it has problems with spaces is because cin only picks up until the first space.  use getline instead

---

### Post by band-aid on 2007-02-14
Ok changed my cin's out ofr getline()'s and it works fine. But now my above command does not. Might it have something to do with the cin.ignore(100,'\n')? Maybe its ignoring too many?

---

### Post by g3k0 on 2007-02-14
Yes this is being caused by cin.ignore.  Just take that out of the program.  What it is doing is ignoring everything up to 100 characters after the input until it finds a new line (\n).  We needed this before because the cin leaves the newline on the input and was messing up the getline.  since we are no longer using cin, that problem is gone so it picks up the next input instead.

so just erase it and it should work.  You had the right idea.  You should try things out before asking.  Play around a little.  You learn more that way.

---

### Post by band-aid on 2007-02-14
Yep! that go it. Thanks a lot for all your help.

---

