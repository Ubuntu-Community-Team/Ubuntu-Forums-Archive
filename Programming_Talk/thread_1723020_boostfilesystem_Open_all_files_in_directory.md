---
title: "boost::filesystem Open all files in directory"
date: 2011-04-06
forum: Programming Talk
---

### Post by ciphermagi on 2011-04-06
I am having an issue opening all of the files in a certain directory using boost. Below is the relevant code:
```
class characterSet {
    vector<int> x;
    list<character*> characters;
    list<character*>::iterator it;
    character *tempChar;
    string name, comp, tempStr;
    int selection, dice, tempInt;
    ofstream mySaveFile;
    ifstream myOpenFile;
    ostringstream fileName;
    void deleteChars();
    void saveChars();
    void openChars();
    void printChars();
    void rollChars();
    character * newCharacter();
public:
    void showMenu();
};

void characterSet::openChars(){
    vector<boost::filesystem::path> v;
    vector<boost::filesystem::path>::iterator iter;
    const boost::filesystem::path p(/*"/home/ciphermagi/Documents/OOP/Michael/save/"*/"save/");
    try{
        if(exists(p) && is_directory(p)){
            copy(boost::filesystem::directory_iterator(p), boost::filesystem::directory_iterator(p), back_inserter(v));
            sort(v.begin(), v.end());
            for(iter = v.begin(); iter != v.end(); ++iter){
                myOpenFile.open(iter->filename()); //This line is broken
                it = characters.begin();
                while(!myOpenFile.eof()){
                    myOpenFile >> name;
                    for(int i = 0; i < 9; i++){
                        myOpenFile >> tempInt;
                        x.push_back(tempInt);
                    }
                tempChar = new character(name, x);
                cout << "Successfully loaded " << tempChar->charName << endl;
                characters.push_back(tempChar);
                x.clear();
                }
                myOpenFile.close();
            }
        }
        else {cout << p << "does not exist.\n";}
    }
    catch(const boost::filesystem::filesystem_error& ex){
        cout << ex.what() << "\n";
    }
}
```The commented line is the line that my linker is pointing to as being bad, with the following output:
> /home/*****/Documents/OOP/*****/main.cpp||In member function ‘void characterSet :: openChars()’: |[FONT=monospace]
[/FONT]/home/*****/Documents/OOP/*****/main.cpp|143|error: no matching function for call to ‘std :: basic_ifstream<char, std :: char_traits<char> > :: open(boost :: filesystem3 :: path)’|[FONT=monospace]
[/FONT]/usr/include/c++/4.4/fstream|525|note: candidates are: void std :: basic_ifstream<_CharT, _Traits> :: open(const char*, std :: _Ios_Openmode) [with _CharT = char, _Traits = std :: char_traits<char>]|
||=== Build finished: 1 errors, 0 warnings ===|I've tried converting it into a c_str, as well as using stringstream to stuff a c_str() and then open the output variable from the stringstream. That returned this output:
> main.cpp|| undefined reference to `boost :: filesystem3 :: path :: filename() const'|Anybody have any ideas?

---

### Post by GeneralZod on 2011-04-06
The fact std::fstream doesn't accept std::string has always baffled me, but yes, you are correct in that you need to use c_str().

The linker error suggest that you need to link in the Boost filesystem library, which you can probably do by adding something along the lines of 

```
-lboost_filesystem
```

to your linker flags.

Edit:

Oh, some interesting discussion about fstream and string:

[http://stackoverflow.com/questions/32332/why-dont-the-stdfstream-classes-take-a-stdstring](http://stackoverflow.com/questions/32332/why-dont-the-stdfstream-classes-take-a-stdstring)

---

### Post by ciphermagi on 2011-04-06
Actually, my #include includes the literal filepath from root of my boost libraries, so I don't think it's a linkage problem.

---

### Post by SledgeHammer_999 on 2011-04-06
> **ciphermagi said:**
> Actually, my #include includes the literal filepath from root of my boost libraries, so I don't think it's a linkage problem.

You also need to specifically link against the library itself. The header files(through the includes) are just instructions for the compiler/linker on what to expect from the lib or what to search in the lib.

NOTE: Many of the boost libs are headers-only, meaning you don't need an extra library file. Boost.Filesystem isn't one of those. It creates a small library file that you need to link to.(dynamically or statically).

---

