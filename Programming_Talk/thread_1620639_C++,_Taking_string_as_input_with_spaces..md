---
title: "C++, Taking string as input with spaces."
date: 2010-11-13
forum: Programming Talk
---

### Post by cgroza on 2010-11-13
Hello, 

I need to get the user input as a string with spaces contained in it. I ahve been told to use get line like this: getline(cin,var);

But the getline skips like its not there. Here is my code:

```
phrase = "";
                        
            while (phrase == ""){
            sentence = "";
            cout<<"Enter phrase to decrypt:"<<endl;
            getline(cin,phrase);
            for (size_t i = 0; i < phrase.length(); ++i)
```

I am begginer in C++. I just need a way to take a string with spaces and pass it further in a for loop.
Thank you.

---

### Post by GeneralZod on 2010-11-13
Post compilable code and an input string that demonstrates the problem, please :)

---

### Post by cgroza on 2010-11-13
OK.
```

#include <cstdlib>
#include <iostream>
#include <stdio.h>
#include <string.h>
#include <fstream>


void cleaner(){
    using namespace std;
       system("clear");
}

int main(int argc, char *argv[]){
    using namespace std;
    string warn,warn2,sentence,phrase,silent,info,passy,ask,askfor,askfor2,hold,pas,pas1,activlog,logchoice;
    char letter, paschoice;

     
    
    ifstream test;
    test.open("/home/cgroza/.declog.dat");
    
    if (test){activlog = "True";}
    else{activlog = "False";}
    test.close();
    
    FILE* check = fopen("/home/cgroza/.rempas++","r");
    if(!check){
    ifstream password;
    password.open("/home/cgroza/.decryptorc++.dat");
    if (password){
    password>>pas;
    pas1 = "False";
    int n;
    n = 0;
    while (pas != pas1){
          if (n == 4){abort();} 
          cout<<"Enter Password: ";
          cin>>pas1;
          if (pas1 == pas){password.close(); break;}
          else{cout<<"Wrong"<<endl; n++;}  
 
            }
   }
   else{
       askfor = "True";
       askfor == "False";
       while (askfor != askfor2){
           cout<<"No password found.\nEnter password: ";
           cin>>askfor;
           cout<<"Enter again: ";
           cin>>askfor2;
           ofstream password;
           password.open("/home/cgroza/.decryptorc++.dat");
           password << askfor2 ;
           password.close();
       }
    }
  }

    while (1 == 1){
    cleaner();
    cout << "1 to encrypt.\n2 to decrypt.\n9 for log management.\n0 for password management.\nq to exit\n1/2/0/q: ";
    cin>>ask;
    if (ask == "q")
    break;

    
    if (ask == "9"){
        while(logchoice != "1" || logchoice != "2" || logchoice != "3" || logchoice != "4" || logchoice != "0"){
            cleaner();
            cout<<"1 to view log.\n2 to erase log.\n3 to enable log.\n4 to disable log.\n0 to go back.\n1/2/3/4/0: ";
            cin>>logchoice;
            
            if (logchoice == "1"){
                string content;
                if (activlog == "True"){
                ifstream log;
                log.open("/home/cgroza/.declog.dat");
                while (!log.eof()){getline(log,content);cout<<content<<endl;}
                cout<<"Enter Something and Press <enter>.";
                cin>>hold;
                cleaner();
              }    
            }
            
            if (logchoice == "2"){
                string sure;
                while(sure != "y" && sure!= "n"){
                cout<<"Are you sure?y/n: ";    
                cin>>sure;
                if (activlog == "True" && sure == "y"){
                    ofstream log;
                    log.open("/home/cgroza/.declog.dat");
                    log.close();
                    cleaner();
                    break;
                    }

                }
              }
            if (logchoice == "3"){
                if (activlog == "False"){
                    ofstream log;
                    log.open("/home/cgroza/.declog.dat");
                    log<<"dude";
                    log.close();
                    }
                }
            
            
            if (logchoice == "4"){
                if (activlog == "True"){remove("/home/cgroza/.declog.dat");}
                }
            
            if (logchoice == "0"){
            cleaner();
            break;
            } 
            
            
            }
        }
    
    
    if (ask == "0"){
        while (paschoice != '1' || paschoice != '2' || paschoice != '3' || paschoice != '0'){
        cleaner();
        cout<<"1 to enable password.\n2 to disable password.\n3 to change password.\n0 to go back.\n1/2/3/0:";
        cin>>paschoice;
            
            if (paschoice == '1')
               remove("/home/cgroza/.rempas++");
               
            
            if (paschoice == '2')
            {

               ofstream  rempas;
               rempas.open("/home/cgroza/.rempas++");
               rempas<<"";
               rempas.close();   

             }
            if (paschoice == '3')
            {
               askfor = "True";
               askfor2 = "False";
               while (askfor != askfor2){
                 ofstream password;
                 password.open("/home/cgroza/.decryptorc++.dat");
                 cout<<"Enter new password: ";
                 cin >> askfor;
                 cout<<"Enter again: ";
                 cin >> askfor2;
                 if (askfor == askfor2){
                     password << askfor;
                     password.close();
         }             
       }
      break;
     }
   if (paschoice == '0')
      break;
   
  }
}

    while (ask =="1" || ask == "2"){
        if (ask == "1"){

            phrase = "";
            while (phrase == ""){

              sentence = "";
              cout<<"Enter phrase to encrypt:"<<endl;
              getline(cin,phrase);
              
              for (size_t i = 0; i < phrase.length(); ++i){
                  letter = phrase[i];


                if (isspace(letter))
                    sentence = sentence + ' ';
                 
                if (letter == 'a')
                    sentence = sentence + '~' ;
                else if (letter == 'b')
                    sentence = sentence + '@' ;

                else if (letter == 'c')
                    sentence = sentence + '#' ;

                else if (letter == 'd')
                    sentence = sentence + '$' ;

                else if (letter == 'e')
                    sentence = sentence + '%' ;

                else if (letter == 'f')
                    sentence = sentence + '^' ;

                else if (letter == 'g')
                    sentence = sentence + '&' ;

                else if (letter == 'h')
                    sentence = sentence + '*' ;

                else if (letter == 'i')
                    sentence = sentence + '(' ;

                else if (letter == 'j')
                    sentence = sentence + '{' ;

                else if (letter == 'k')
                    sentence = sentence + ')' ;

                else if (letter == 'l')
                    sentence = sentence + '_' ;

                else if (letter == 'm')
                    sentence = sentence + '-' ;

                else if (letter == 'n')
                    sentence = sentence + '+' ;

                else if (letter == 'o')
                    sentence = sentence + '=' ;

                else if (letter == 'p')
                    sentence = sentence + '|' ;

                else if (letter == 'q')
                    sentence = sentence + '\\' ;

                else if (letter == 'r')
                    sentence = sentence + ',' ;

                else if (letter == 's')
                    sentence = sentence + '<' ;

                else if (letter == 't')
                    sentence = sentence + '.' ;

                else if (letter == 'u')
                    sentence = sentence + '>' ;

                else if (letter == 'v')
                    sentence = sentence + '/' ;

                else if (letter == 'w')
                    sentence = sentence + '?' ;

                else if (letter == 'x')
                    sentence = sentence + ';' ;

                else if (letter == 'y')
                    sentence = sentence + ':' ;

                else if (letter == 'z')
                    sentence = sentence + ']';
               
                else if (isdigit(letter))
                  sentence = sentence + letter;
                
                else {
                    sentence = sentence+ '`'+letter;
                    }

      
      }
       

       cout<< sentence<<endl;
       if (activlog == "True"){
       ofstream log;
       log.open("/home/cgroza/.declog.dat",ios::app);
       log<<"\n"<<phrase<<"\n"<<sentence<<"\n";
       log.close();}
         break;     

    }
    cout<<"Enter Something and Press <enter>.";
    cin>>hold;
    break; 
  }
 
        if (ask == "2"){
            phrase = "";
                        
            while (phrase == ""){
            sentence = "";
            cout<<"Enter phrase to decrypt:"<<endl;
            getline(cin,phrase);
            for (size_t i = 0; i < phrase.length(); ++i)
 {              letter = phrase[i];
 
 
                if (isspace(letter))
                        sentence = sentence + ' ';
                
                if (letter == '`'){
                       warn = "True";
                       }


                if (warn == "True"){
                   i=i+1;
                   letter = phrase[i];
                   sentence = sentence+letter;
                   warn2 = "True";

                }
                
                if (warn2 != "True"){
               

                    if (letter == '~')
                        sentence = sentence + 'a';

                    else if (letter == '@')
                        sentence = sentence + 'b' ;

                    else if (letter == '#')
                        sentence = sentence + 'c' ;

                    else if (letter == '$')
                        sentence = sentence + 'd' ;

                    else if (letter == '%')
                        sentence = sentence + 'e' ;

                    else if (letter == '^')
                        sentence = sentence + 'f' ;

                    else if (letter == '&')
                        sentence = sentence + 'g' ;

                    else if (letter == '*')
                        sentence = sentence + 'h' ;

                    else if (letter == '(')
                        sentence = sentence + 'i' ;

                    else if (letter == ')')
                        sentence = sentence + 'k' ;

                    else if (letter == '{')
                        sentence = sentence + 'j';

                    else if (letter == '_')
                        sentence = sentence + 'l' ;

                    else if (letter == '-')
                        sentence = sentence + 'm' ;

                    else if (letter == '+')
                        sentence = sentence + 'n' ;

                    else if (letter == '=')
                        sentence = sentence + 'o' ;

                    else if (letter == '|')
                        sentence = sentence + 'p' ;

                    else if (letter == '\\')
                        sentence = sentence + 'q' ;

                    else if (letter == ',')
                        sentence = sentence + 'r' ;

                    else if (letter == '<')
                        sentence = sentence + 's';

                    else if (letter == '.')
                        sentence = sentence + 't';

                    else if (letter == '>')
                        sentence = sentence + 'u';

                    else if (letter == '/')
                        sentence = sentence + 'v';

                    else if (letter == '?')
                        sentence = sentence + 'w';

                    else if (letter == ';')
                        sentence = sentence + 'x';

                    else if (letter == ':')
                        sentence = sentence + 'y';

                    else if (letter == ']')
                        sentence = sentence + 'z';

                    

                    else if (isdigit(letter))
                        sentence = sentence + letter;


                }
                }
              warn2= "False";  
              cout<<sentence<<endl;  
              if (activlog == "True"){
              ofstream log;
              log.open("/home/cgroza/.declog.dat",ios::app);
              log<<"\n"<<sentence<<"\n"<<phrase<<"\n";
              log.close();}
              break;
              }

              cout<<"Enter Something and Press <enter>.";
              cin>>hold;
              break;
            }
          }
        }
      }
```

Input string: Uhmm, before I used cin>>variable to get input, and it took the input but the program choked with spaces.

---

### Post by cgroza on 2010-11-13
Anyone?

---

### Post by dwhitney67 on 2010-11-13
Rather than post a long, rambling, sequence of code, could you not whittle the problem down to a few lines of code?

Screw it... here, test with this:
```

#include <iostream>
#include <string>

int main()
{
   std::string fullname;

   std::cout << "Enter your first and last name: ";
   std::getline(std::cin, fullname);

   std::cout << "Hello " << fullname << std::endl;
}

```

---

### Post by cgroza on 2010-11-13
> **dwhitney67 said:**
> Rather than post a long, rambling, sequence of code, could you not whittle the problem down to a few lines of code?

Screw it... here, test with this:
```

#include <iostream>
#include <string>

int main()
{
   std::string fullname;

   std::cout << "Enter your first and last name: ";
   std::getline(std::cin, fullname);

   std::cout << "Hello " << fullname << std::endl;
}

```

This is what I am doing. It acts like getline is not there.

---

### Post by cgroza on 2010-11-13
Fiixed it. Thank you.

---

### Post by dwhitney67 on 2010-11-13
> **cgroza said:**
> Fiixed it. Thank you.

Btw, I did see the error below; is this what you fixed?
```

askfor == "False";

```

---

### Post by cgroza on 2010-11-13
> **dwhitney67 said:**
> Btw, I did see the error below; is this what you fixed?
```

askfor == "False";

```

No. That has nothing to do with my getline not doing its job, but thanks for pointing it. That is there for making a test condition valid. I know its weird, but I put 2 lines of "getline" on after another and now it works as expected. I do not understand this. Now it looks like this and it works:

getline(cin,phrase);
getline(cin,phrase);
Thanks.

---

### Post by dwhitney67 on 2010-11-13
You need to understand why your kludge worked.  I'll bet that before you attempted to read in 'phrase', you probably read in some other non-string (eg. int) data.

After you read in non-string data, it is your responsibility (if you find it necessary) to retrieve all characters from the standard-in stream that remain, most notably the newline character.  So as an example, the following will fail:
```

int    number;
string str;

cout << "Enter a number: ";
cin  >> number;             // gets number, but newline remains in the stream

cout << "Enter a string: "
getline(cin, str);          // will be executed, but will capture newline

```

To "bleed" the standard-in stream, something like the following is used:
```

cin.ignore(numeric_limits<streamsize>::max(), '\n');

```
This dumps all characters in the cin stream up to and including, the newline character OR until the given number of characters have been dumped.  Write yourself a little program to experiment with it.

---

### Post by cgroza on 2010-11-13
Ohh! It all makes sense now. Thank you very much. I'll study the getline more.

---

