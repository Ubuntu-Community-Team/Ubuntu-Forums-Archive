---
title: "extract files from large uncompressed file"
date: 2008-08-12
forum: Programming Talk
---

### Post by flostre on 2008-08-12
Hi.

I have a large file which (I strongly suspect) is a simple concatenation of many small files (PNG, JPEG, CSS,...). I already wrote a c++ program that splits the file whenever it encounters a PNG-header (see below). This worked somewhat, meaning many of the resulting files were valid PNGs. However, since I discovered that there are also other filetypes involved, I hesitate to extend it. I am suspecting that there already is a program/combination of tools to extract a long list of known file types.

Unfortunately I cannot post an example data-file since they are copyright protected.

flostre

The PNG extraction:

```

/*
known issue: cannot detect header if it is split between chunks
work-around: run program on resulting files
*/

#include <iostream>
#include <fstream>
#include <sstream>
#include <iomanip>

using namespace std;

#define HEADER_LENGTH 8

bool hasHeader( unsigned char* text, int index ) {
  return text[index]==0x89 
    && text[index+1]=='P' && text[index+2]=='N' && text[index+3] == 'G'
    && text[index+4]==0x0d && text[index+5]==0x0a && text[index+6] == 0x1a
    && text[index+7]==0x0a;
}

int main( int argc, char* argv[] ) {

  ifstream file( argv[1] );
  int outIndex=0;
  ostringstream oss;
  oss << "out" << setw(4) << setfill('0') << outIndex << ".png";
  ofstream* outFile= new ofstream ( oss.str().c_str() );

  int bufSize=2048;
  int readSize=0;
  unsigned char* buf = new unsigned char[bufSize];


  while( ! file.eof() ) {
    file.read( (char*)buf, bufSize );
    readSize = file.gcount();

    unsigned lastIndex=0;
    for(int i=0; i<readSize-HEADER_LENGTH; ++i ) {
      if( hasHeader( buf, i ) ) {
	outFile->write( (char*)buf+lastIndex, (i-lastIndex) );
	outFile->close();
	delete outFile;
	outFile=0;

	++outIndex;
	oss.str("");
	oss << "out" << setw(4) << setfill('0') << outIndex << ".png";
      	outFile = new ofstream( oss.str().c_str() );

	lastIndex=i;
      }
    }
    if( lastIndex==0 ) {
      (*outFile) << buf;
    } else {
      outFile->write( (char*)buf+lastIndex, readSize-lastIndex );
    }
  }

  delete[] buf;

  return 0;

}

```

---

### Post by KingTermite on 2008-08-12
Are you sure its not just tar format? Have you tried a tar command on it?

---

### Post by flostre on 2008-08-18
Thanks, hadn't thought of that. :oops:

It was no tar-ball, but cpio did the trick.

---

