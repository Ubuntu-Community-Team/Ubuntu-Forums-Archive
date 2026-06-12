---
title: "Error in opening file C++"
date: 2009-12-12
forum: Programming Talk
---

### Post by forstudy3 on 2009-12-12
Hi,
I have written a function which will open the file with the input name provided.I am compiling on a Linux box using g++ compiler.Detail code below Plz let me know what is the wrong in code.

```
1  #include<iostream>
      2  #include<fstream>
      3  #include<string>
      4  #include<stddef.h>
      5  #include<cstddef>
      6  #include<cstring>
      7
      8  using namespace std;
      9
     10  int main ()
     11 {
     12 string file1,file2;
     13 string file3;
     14
     15 fstream OpFile(string,ios_base::openmode);
     16
     17 cout << "Enter File Names"<<"\n";
     18 getline(cin,file1);
     19 getline(cin,file2);
     20 getline(cin,file3);
     21
     22 fstream INPUT1;
     23 fstream INPUT2;
     24 fstream INPUT3;
     25
     26 INPUT1 =  OpFile(file1, ios::in | ios::binary);
     27 INPUT2 =  OpFile(file2, ios::in);
     28 INPUT3 = OpFile (file3, ios::out);
     29
     30
     31 INPUT1.close();
     32 INPUT2.close();
     33 INPUT3.close();
     34
     35 return 0;
     36 }
     37
     38      fstream OpFile (string filename, ios_base::openmode mode)
     39     {
     40          fstream file;
     41
     42         file.open (filename.c_str(), mode);
     43         return file;
     44     }
```Error message I m getting is-

[html]ex.cpp: In function `int main()':
ex.cpp:26: error: no match for 'operator=' in 'INPUT1 = OpenFile(std::string, std::_Ios_Openmode)(std::operator|( _S_in,  _S_bin))'
/usr/lib/gcc/i386-redhat-linux/3.4.3/../../../../include/c++/3.4.3/iosfwd:90: note: candidates are: std::basic_ifstream<char, std::char_traits<char> >& std::basic_ifstream<char, std::char_traits<char> >::operator=(const std::basic_ifstream<char, std::char_traits<char> >&)
ex.cpp: In copy constructor `std::basic_ios<char, std::char_traits<char> >::basic_ios(const std::basic_ios<char, std::char_traits<char> >&)':[/html]/usr/lib/gcc/i386-redhat-linux/3.4.3/../../../../include/c++/3.4.3/bits/ios_base.h:781: error: `std::ios_base::ios_base(const std::ios_base&)' is private

---

### Post by cariboo on 2009-12-14
A bump for the move.

---

### Post by MadCow108 on 2009-12-14
you are not allowed to copy streams
that why the copy operators are private

for what reason would you want to do that anyway?

instead pass the open function a reference to an existing stream
(I hope you have a reason for encapsulating the open function of streams in the first place)

---

### Post by dwhitney67 on 2009-12-14
I don't believe you are allowed to copy an fstream object (ie. it is non-copyable).

Read up on passing by reference, both for the fstream and your string objects.

P.S.  Or by pointer.

```

std::fstream* OpFile(**const std::string&** filename, **const std::ios_base::openmode&** mode);

int main()
{
   ...

   **fstream*** INPUT1 = OpFile(file1, ios::in | ios::binary);

   ...
}

std::fstream* OpFile(**const std::string&** filename, **const std::ios_base::openmode&** mode)
{
   return new std::fstream(filename.c_str(), mode);
}

```

P.S. #2  What is the point of the OpFile() function??  Is it to merely add another layer of abstraction to the code?

---

