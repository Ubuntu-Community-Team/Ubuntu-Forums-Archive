---
title: "C++ Wierd Output"
date: 2009-09-19
forum: Programming Talk
---

### Post by matmatmat on 2009-09-19
I have this program:
```

#include <unistd.h>
#include <iostream>
#include <string>
#include <fstream>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

using namespace std;

void add(char todo[], string priority, string tag, string date, string in, string home){
    FILE *file;
    file = fopen(home.c_str(), "a");
    fprintf(file, "%-50s| %-6s| %-30s| %-12s| %-s\n", todo, priority.c_str(), tag.c_str(), date.c_str(), in.c_str());
    fclose(file);
}

string get_element(string line, int n){
    int i;
    string tag;
    for (i = n; line[i] != '\0'; i++){
        if (line[i] == ' ' && line[i + 1] == ' '){
            break;
        }
        tag += line[i];
    }
    return tag;
}

void check_date(string home, string date){
    string line;
    fstream file(home.c_str(),ios::in);
    int i = 0;
    if (file.is_open()){
          while( getline( file, line ) ) {
            string f_date = get_element(line, 106);
            if (f_date == date){
                cout << "TODO: '" << get_element(line, 0) << "' is due in TODAY!\n";
            }
          }
    }    
}

void filter(string home, int priority){
    string line;
    fstream file(home.c_str(),ios::in);
    int i = 0;
    bool print;
    if (file.is_open()){
          while( getline( file, line ) ) {
            const char *cline = line.c_str();
            string pr;
            if (cline[52] == '1'){
                pr = "High  ";
            }
            else if (cline[52] == '2'){
                pr = "Medium";
            }
            else if (cline[52] == '3'){
                pr = "Low   ";
            }
            if (atoi(&cline[52]) == priority){
                print = true;
            }
            else{
                print = false;
            }
            if (print){
                int i2;
                cout << "[" << i << "] ";
                for (i2 = 0; i2 <= 51; i2++){
                    cout << cline[i2];
                }
                cout << pr;
                for (i2 = 53; cline[i2] != '\0'; i2++){
                    cout << cline[i2];
                }
                cout << "\n";           
            }
            i++;
        }
    }
    file.close();
}

void filter_by_tag(string home, string tag){
    string line;
    fstream file(home.c_str(),ios::in);
    int i = 0;
    bool print;
    if (file.is_open()){
          while( getline( file, line ) ) {
            const char *cline = line.c_str();
            string pr;
            if (cline[52] == '1'){
                pr = "High  ";
            }
            else if (cline[52] == '2'){
                pr = "Medium";
            }
            else if (cline[52] == '3'){
                pr = "Low   ";
            }
            if (get_element(line, 60) == tag){
                print = true;
            }
            else{
                print = false;
            }
            if (print){
                int i2;
                cout << "[" << i << "] ";
                for (i2 = 0; i2 <= 51; i2++){
                    cout << cline[i2];
                }
                cout << pr;
                for (i2 = 53; cline[i2] != '\0'; i2++){
                    cout << cline[i2];
                }
                cout << "\n";           
            }
            i++;
        }
    }
    file.close();
}

[B]void column_filter(bool one, bool two, bool three, bool four, bool five, string home){
    string line;
    fstream file(home.c_str(),ios::in);
    int i = 0;
    if (file.is_open()){
          while( getline( file, line ) ) {
            const char *cline = line.c_str();
            string pr;
            if (cline[52] == '1'){
                pr = "High  ";
            }
            else if (cline[52] == '2'){
                pr = "Medium";
            }
            else if (cline[52] == '3'){
                pr = "Low   ";
            }
            int i2;
            cout << "[" << i << "] ";
            if (one){
                for (i2 = 0; i2 <= 50; i2++){
                    cout << cline[i2];
                }
            }
            if (two){
                cout << " ";
                cout << pr;
                for (i2 = 53; cline[i2] <= 58; i2++){
                    cout << cline[i2];
                }                 
            }
            if (three){
                for (i2 = 59; cline[i2] <= 89; i2++){
                    cout << cline[i2];
                } 
            }
            if (four){
                for (i2 = 91; cline[i2] <= 104; i2++){
                    cout << cline[i2];
                }                 
            }
            if (five){
                for (i2 = 105; cline[i2] != '\0'; i2++){
                    cout << cline[i2];
                }                  
            }   
            cout << "\n";           
            i++;
        }
    }
    file.close();    
}[/B]

void list(string home){
    string line;
    fstream file(home.c_str(),ios::in);
    int i = 0;
    if (file.is_open()){
          while( getline( file, line ) ) {
            const char *cline = line.c_str();
            string pr;
            if (cline[52] == '1'){
                pr = "High  ";
            }
            else if (cline[52] == '2'){
                pr = "Medium";
            }
            else if (cline[52] == '3'){
                pr = "Low   ";
            }
            int i2;
            cout << "[" << i << "] ";
            for (i2 = 0; i2 <= 51; i2++){
                cout << cline[i2];
            }
            cout << pr;
            for (i2 = 53; cline[i2] != '\0'; i2++){
                cout << cline[i2];
            } 
            cout << "\n";           
            i++;
        }
    }
    file.close();
}

void clear(string home){
    FILE *file;
    file = fopen(home.c_str(), "w");
    fprintf(file, "");
    fclose(file);
}

void remove(string home, int n){
    string f;
    string line;
    fstream file(home.c_str(),ios::in);
    int i = 0;
    if (file.is_open()){
          while( getline( file, line ) ) {
            if (i != n){
                f += line;
                f += '\n';
            }
            i++;
        }
    }
    file.close();    
    clear(home);
    fstream fileo(home.c_str(),ios::out);    
    fileo << f;
}

void remove_a_few(string home, int bot, int top){
    string f;
    string line;
    fstream file(home.c_str(),ios::in);
    int i = 0;
    if (file.is_open()){
          while( getline( file, line ) ) {
            if (i >= bot && i <= top){

            }
            else{
                f += line;
                f += '\n';                
            }
            i++;
        }
    }
    file.close();    
    clear(home);
    fstream fileo(home.c_str(),ios::out);    
    fileo << f;
}

void help(){
    cout << "Usage:\n";
    cout << "\tt-do [options]\n";
    cout << "Options:\n";
    cout << "\t-a [TODO]\n";
    cout << "\t\tAdd a todo with summary TODO\n";
    cout << "\t-p [Priority]\n";
    cout << "\t\tAdd a priority - must come before '-a'\n";
    cout << "\t-f [NUM/TAG]\n";
    cout << "\t\tFilter TODOs by the priority (NUM) or tag (TAG)\n";
    cout << "\t-r [NUM]\n";
    cout << "\t\tRemove TODO #NUM\n";
    cout << "\t-t [TAG]\n";
    cout << "\t\tAdd a tag - must come before '-a'\n";
    cout << "\t-d [DD/MM/YY]\n";
    cout << "\t\tAdd a start date to the TODO - must come before '-a'\n";
    cout << "\t-i [DD/MM/YY]\n";
    cout << "\t\tAdd a date for the TODO to be finished - must come before '-a'\n";    
    cout << "\t-l\n";
    cout << "\t\tList TODOs\n";
    cout << "\t-c\n";
    cout << "\t\tClear all TODOs\n";
    cout << "\t-h\n";
    cout << "\t\tShow this message\n";
    cout << "Examples:\n";
    cout << "\tt-do -r 1-3\n";
    cout << "\t\tremove TODOs 1, 2 & 3\n";
    cout << "\tt-do -p 1 -t \"Home\" -i \"10/10/09\" -a \"Finish writing stuff\"\n";
    cout << "\t\t add a TODO with High priority, that is tagged with 'home', the due date is '10/10/09' & the summary is 'Finish writing stuff'\n";
}
int main (int argc, char* argv[]) {
    string home(getenv("HOME"));
    string todo = "/.todo.txt";
    string priority = "2";  
    string tag = "Work";   
    home = home + todo;
    int opt;
    int n;
    int priorityf;
    char outstr[200];
    int i;
    time_t t;
    bool one = false;
    bool two = false;
    bool three = false;
    bool four = false;
    bool five = false;    
    struct tm *tmp;
    t = time(NULL);
    tmp = localtime(&t);
    strftime(outstr, sizeof(outstr), "%d/%m/%y", tmp);
    string date = outstr;   
    string in; 
    check_date(home, date);    
    while ((opt = getopt(argc,argv, "a:p:f:r:t:d:i:o:lhc")) !=EOF ){
        switch (opt){  
[B]            case 'o':
                for (i=0;optarg[i] != '\0';i++){
                    switch (optarg[i]){
                        case '1':
                            one = true;
                            break;
                        case '2':
                            two = true;
                            break;
                        case '3':
                            three = true;
                            break;
                        case '4':
                            four = true;
                            break;
                        case '5':
                            five = true;
                            break;
                    }
                }
                column_filter(one,two,three,four,five,home);
                break;[/B]
            case 'd':
                date = optarg;
                break;
            case 'i':
                in = optarg;
                break;
            case 'p':
                priority = optarg;
                break;
            case 't':
                tag = optarg;
                break;
            case 'a': 
                add(optarg, priority, tag, date, in, home); 
                break; 
            case 'l':
                list(home);
                break;
            case 'c':
                clear(home);
                break;
            case 'r':
                if (optarg[1] == '-'){
                   remove_a_few(home, atoi(&optarg[0]), atoi(&optarg[2]));
                   break;
                }
                n = atoi(optarg);
                remove(home, n);
                break;
            case 'h':
                help();
                break;
            case 'f':
                priorityf = atoi(optarg);
                if (priorityf != 0){
                    filter(home, priorityf);
                    break;
                }
                filter_by_tag(home, optarg);
                break;
            case '?':
                help();
                break;      
        }
    }
    return 0;
}

```
it reads in a file like this:
```

Make this program filter out columns              | 1     | Programming                   | 19/09/09    | 
Make this program call add at the end             | 1     | Programming                   | 19/09/09    | 
H                                                 | 2     | W                             | 19/09/09    | 

```
it should be run like this:
```

-r "123"

```
when you do this it outputs:
```

[0] Make this program filter out columns              | High        P
[1] Make this program call add at the end             | High        P
[2] H                                                 | Medium      W 

```
it isn't reading all the characters here:
```

            if (three){
                for (i2 = 59; cline[i2] <= 89; i2++){
                    cout << cline[i2];
                } 
            }

```
but why?
Sorry if this is confusing

---

### Post by januzi on 2009-09-19
So, You have got condition:
cline[i2] <= 58 (89 and 104)

It means that You loop string until You find a char bigger than 58 (89 and 104) which gives us ":", "Y" and "h". You could check loop:
for (i2 = 59; i2 <= 89; i2++)

---

### Post by MadCow108 on 2009-09-19
I don't understand the loop
why are you looping from 59(;) to 89(Z) and checking if that position is smaller Z?
if there is no Z it will just go one until it reaches the end of cline and probably crash

I would suggest using iostreams to parse such kind of files. should be a lot easier
especially fetching a certain column is a trivial operation with streams

---

### Post by matmatmat on 2009-09-19
Thanks, I didn't notice i was checking against the value of the array

---

### Post by MadCow108 on 2009-09-19
so you have hardcoded column lengths.
you should change that, it makes your program very unflexible.

do something like that:
```

ifstream file("file");
string line;
while (getline(file,line)) {
  stringstream linestream(line);
  string column;
  while (getline(linestream,column,'|')) {
    // do something  with the column
  }
}

```

---

