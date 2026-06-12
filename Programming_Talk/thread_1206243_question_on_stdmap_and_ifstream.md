---
title: "question on std::map and ifstream"
date: 2009-07-06
forum: Programming Talk
---

### Post by monkeyking on 2009-07-06
I've written the following working program.
That creates an array of objects that reads a specific number of lines from all files (sequentially) and then inputs these into a map<linenum,all_the_at_linenum_in_all_files>.
forexample:

[PHP]
cat file0.txt
0 file0 line0
1 file0 line1
2 file0 line2
3 file0 line3
[/PHP]
[PHP]
cat file1.txt
0 file1 line0
1 file1 line1
2 file1 line2
3 file1 line3
4 file1 line4
[/PHP]

[PHP]
./a.out
initializingfile : file0.txt
initializingfile : file1.txt

----------------
0:      numFiles: 2     0 file0 line0   0 file1 line0
1:      numFiles: 2     1 file0 line1   1 file1 line1
2:      numFiles: 2     2 file0 line2   2 file1 line2
3:      numFiles: 2     3 file0 line3   3 file1 line3
----------------

----------------
4:      numFiles: 1     4 file1 line4
----------------
[/PHP]

To clarify the code I don't cleanup memory, and I'm aware of this fact.

I've got 2. questions, can I trust that the currentlinepos for each ifstream object stays put when I use  another of instance of my reader?

Secondly, can I trust that the std::map gets cleaned up automaticly? Or should I force std::map.clear() between looping up and creating a new std::map. I know that  the c++ specification says that it should happen, but will the compiler optimization might wait untill later in the program instead of doing it on each loop? 

If anyone can spot something blatantly wrong with the code I very open for suggestions :)
[PHP]
#include <iostream>
#include <map>
#include <vector>
#include <cstring>
#include <fstream>
#include <utility>

#define LENS 100 //the max number of bytes per line
typedef std::map<unsigned int, std::vector<char*>  > aMap;


void printMap(const aMap& asso){
  if(asso.size()!=0){
    printf("\n----------------\n");
    for(aMap::const_iterator it = asso.begin(); it != asso.end(); ++it){
      int p = it->first;
      std::cout << p << ":\t";

      std::vector<char*> vec = it->second;
      std::cout<<"numFiles: " <<vec.size() << "\t";
      for(unsigned int i=0; i<vec.size() ;i++)
        std::cout << vec[i] << "\t";
      std::cout<< std::endl;
    }
    printf("----------------\n");
  }
}


class reader{
  int id;
public:

  const char* filename;
  std::ifstream os;
  int linenum;
  int readlines(int numlines,aMap &asso);
  void init(int num,const char *fname);
  int close() {printf("closing:%s\n",filename);os.close();return linenum;}
};

void reader::init(int num,const char *fname){
  printf("initializingfile : %s\n",fname);
  linenum = 0;
  filename = fname;
  os.open(filename);
  id=num;
}




int reader::readlines(int numlines,aMap &asso){
  char aline[LENS];
  aMap::iterator it;
  int i=0;
  while(i<numlines && !os.eof() ){
    os.getline(aline,LENS);
    if(strlen(aline)!=0){
      //firstly if the linenum hasnt been added we should create a vector
      it=asso.find(linenum);
      if(it==asso.end()){
        std::vector<char*> vec;
        vec.push_back(strdup(aline));
        asso.insert(std::make_pair(linenum,vec));
      }else{
        it->second.push_back(strdup(aline));
        //the element exists so just push the line back in the vector
      }
      linenum++;
      i++;
    }
  }
  return (!os.eof());
}

int sum(int* ary,int len){
  int ret=0;
  for(int i=0;i<len;i++)
    if(ary[i])
      ret++;
  return ret;
}

int main(){
  //basicly just create a char** with the filenames
  int numfiles = 3;
  const char** files = new const char*[3];
  const char* file0 = "file0.txt";
  const char* file1 = "file1.txt";
  const char* file2 = "file2.txt";
  files[0] = file0 ;
  files[1] = file1 ;
  files[2] = file2 ;

  //initalize the filereader objects
  reader* handl = new reader[numfiles];
  int * returnValues = new int[numfiles];
  for(int i=0 ; i<numfiles ;i++){
    handl[i].init(i,files[i]);
    returnValues[i] = 1;
  }

  //keep reading untill all files has send an eof()
  while(sum(returnValues,numfiles)){
    aMap asso;
    for(int i=0 ; i<numfiles ;i++){
      if(returnValues[i])
        returnValues[i]=handl[i].readlines(2,asso);

    }
    printMap(asso);
    //asso.clear() SHOULD I DO THIS?
  }

  return 0;
}









[/PHP]

---

### Post by Zugzwang on 2009-07-07
> **monkeyking said:**
> 
I've got 2. questions, can I trust that the currentlinepos for each ifstream object stays put when I use  another of instance of my reader?

It's a little bit tough to understand what you are meaning, but the answer is likely to be yes - Try copying a ifstream, as far as I know it doesn't work. "ifstreams" in one instance of your "reader" class are unrelated to those in other classes, so it should work fine. In order to avoid accidental copying of your reader object, let it derive from "boost::noncopyable".

> **monkeyking said:**
> 
Secondly, can I trust that the std::map gets cleaned up automaticly? Or should I force std::map.clear() between looping up and creating a new std::map. I know that  the c++ specification says that it should happen, but will the compiler optimization might wait untill later in the program instead of doing it on each loop? 


No, this is too tough for the compiler optimizer to do as it would require keeping the old map in a different memory position as the new map. As it is not known at compile time how many iterations are being done during execution, this would be problematic as there's no general instance keeping track of allocated memory.

You can trust that the map is properly cleaned up, so all the vector values will be deleted. Note that it is not smart to use char* here as this way, you will have to iterate through the map to get all values and iterate through the values just to delete[] all char* pointers. Don't do it - Use std::string instead, then the memory is automatically cleaned up.

---

### Post by dwhitney67 on 2009-07-07
> **monkeyking said:**
> ...

If anyone can spot something blatantly wrong with the code I very open for suggestions :)

The only thing I found "wrong" with the code is your mix of C and C++, and the over zealous use of the "new" allocator at every opportunity.

I attempted to re-write your code, albeit slightly different in some parts.  My only concern is that using the text data files you posted, I yielded different results.

Here's my code:
[php]
#include <vector>
#include <map>
#include <string>
#include <fstream>
#include <iostream>
#include <algorithm>

typedef std::map<unsigned int, std::vector<std::string> > aMap;

void displayResult(const std::pair<int, std::vector<std::string> >& result);


class Reader
{
public:
   Reader() : m_lineNum(0) {}
   Reader(const Reader& other) : m_lineNum(0) {}

   bool init(const std::string& filename, const unsigned int fileId = 0);
   bool atEOF() const;

   // read the number of lines specified, or if numLines is not specified,
   // read the entire file.
   bool readLines(aMap& asso, const int numLines = -1);

private:
   std::string   m_filename;
   unsigned int  m_id;
   unsigned int  m_lineNum;
   std::ifstream m_fs;
};

bool
Reader::init(const std::string& filename, const unsigned int fileId)
{
   std::cout << "initializing file: " << filename << std::endl;

   m_filename = filename;
   m_id       = fileId;

   m_fs.open(m_filename.c_str());

   return m_fs.good();
}

bool
Reader::atEOF() const
{
   return m_fs.eof();
}

bool
Reader::readLines(aMap& asso, const int numLines)
{
   using namespace std;

   string line;
   int    linesRead = 0;

   while ((numLines == -1 || numLines > 0) && getline(m_fs, line))
   {
      if (line.size() > 0)
      {
         aMap::iterator it = asso.find(m_lineNum);

         if (it == asso.end())
         {
            vector<string> vec;
            vec.push_back(line);
            asso.insert(make_pair(m_lineNum, vec));
         }
         else
         {
            it->second.push_back(line);
         }
      }
      ++m_lineNum;

      if (numLines > 0 && ++linesRead == numLines) break;
   }

   return !atEOF();
}


int main()
{
   using namespace std;

   vector<string> files;

   files.push_back("file0.txt");
   files.push_back("file1.txt");

   vector<Reader> readers(files.size());

   for (size_t i = 0; i < readers.size(); ++i)
   {
      if (readers[i].init(files[i], i) == false)
      {
         cerr << "Error initializing reader with file '" << files[i] << "'." << endl;
         return -1;
      }
   }

   size_t eofCount = 0;

   while (eofCount < readers.size())
   {
      aMap asso;

      for (size_t i = 0; i < readers.size(); ++i)
      {
         if (readers[i].atEOF() == false)
         {
            if (readers[i].readLines(asso, 2) == false)
            {
               ++eofCount;
            }
         }
      }

      cout << "--------------------" << endl;
      for_each(asso.begin(), asso.end(), displayResult);
      cout << "--------------------" << endl;
   }
}


void displayResult(const std::pair<int, std::vector<std::string> >& result)
{
   using namespace std;

   cout << result.first << ":\tnumFiles: " << result.second.size() << "\t";

   for (vector<string>::const_iterator it = result.second.begin(); it != result.second.end(); ++it)
   {
      cout << *it << "\t";
   }
   cout << endl;
}
[/php]

---

### Post by monkeyking on 2009-07-07
Thanks for the clarification Zugzwang

and thanks dwitney  helpfull as usual.


I hadn't really thought about the reader in vectors instead of an array. And keeping the eof status in the objects can proove handy.

---

