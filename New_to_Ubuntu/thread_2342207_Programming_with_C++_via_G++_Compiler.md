---
title: "Programming with C++ via G++ Compiler"
date: 2016-11-04
forum: New to Ubuntu
---

### Post by hakuryuu2 on 2016-11-04
First Post! 
Anyway, I am running 16.04 LTS Ubuntu, and have started to learn my second language on it, C++. I searched up a few guides and downloaded build-essentials, updated the GCC and double checked that I installed G++. After that, I started to make my first program. I used Geany for this, and made a simple program which I copied from "Schaum's Outlines Programming with C++". 
The code for this program named test.cpp:

```

#include <iostream.h>
main()
{
    cout << "Hello World \n";
    return 0;
}

```

When in the compilation process, via the command "g++ test.cpp -o my.test". I made sure that I was in the exact directory via cd when using the terminal, but it originally came up with iostream.h as an error. I looked through the folder and found iostream.h to not be there, so I downloaded iostream.h and inserted it into 5.4.0/ include and the 5.0/include as well. After compiling it again, it came up with no streambuf.h. So I copy and paste a version found on the internet onto Geany and saved it in the .h format to the 5.0 AND 5.4.0 include folders. After that it came with several errors, quoted underneath this post. 

Please help me with this, as I would really like to continue programming
Regards
Haku

```

 In file included from /usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:31:0,
                 from First.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:53:9: error: ‘_G_off_t’ does not name a type
 typedef _G_off_t streamoff;
         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:54:9: error: ‘_G_off_t’ does not name a type
 typedef _G_off_t streampos; // Should perhaps be _G_fpos_t ?
         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:64:5: error: ‘_G_wchar_t’ does not name a type
     _G_wchar_t _fill;
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:144:5: error: ‘_G_wchar_t’ does not name a type
     _G_wchar_t fill() const { return (_G_wchar_t)_fill; }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:145:5: error: ‘_G_wchar_t’ does not name a type
     _G_wchar_t fill(_G_wchar_t newf)
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:249:5: error: ‘streampos’ does not name a type
     streampos _spos; // -2: means that _pos is valid.
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:250:24: error: ‘streampos’ has not been declared
     void set_streampos(streampos sp) { _spos = sp; }
                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘void streammarker::set_streampos(int)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:250:40: error: ‘_spos’ was not declared in this scope
     void set_streampos(streampos sp) { _spos = sp; }
                                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘void streammarker::set_offset(int)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:251:50: error: ‘_spos’ was not declared in this scope
     void set_offset(int offset) { _pos = offset; _spos = (streampos)(-2); }
                                                  ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:251:59: error: ‘streampos’ was not declared in this scope
     void set_offset(int offset) { _pos = offset; _spos = (streampos)(-2); }
                                                           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘int streammarker::saving()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:258:28: error: ‘_spos’ was not declared in this scope
     int saving() { return  _spos == -2; }
                            ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:357:13: error: ‘streampos’ does not name a type
     virtual streampos seekoff(streamoff, _seek_dir, int mode=ios::in|ios:out);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:358:13: error: ‘streampos’ does not name a type
     virtual streampos seekpos(streampos pos, int mode = ios::in|ios:out);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:388:30: error: ‘_G_size_t’ has not been declared
     long sgetline(char* buf, _G_size_t n, char delim, int putback_delim);
                              ^
In file included from /usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:25:0,
                 from /usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:31,
                 from First.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:402:33: error: ‘__gnuc_va_list’ has not been declared
     int vscan(char const *fmt0, _G_va_list ap, ios* stream = NULL);
                                 ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:404:33: error: ‘__gnuc_va_list’ has not been declared
     int vform(char const *fmt0, _G_va_list ap);
                                 ^
In file included from /usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:31:0,
                 from First.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:456:13: error: ‘streampos’ does not name a type
     virtual streampos seekoff(streamoff, _seek_dir, int mode=ios::in|ios:out);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:470:13: error: ‘_G_ssize_t’ does not name a type
     virtual _G_ssize_t sys_read(char* buf, _G_size_t size);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:472:13: error: ‘_G_ssize_t’ does not name a type
     virtual _G_ssize_t sys_write(const void*, long);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘int filebuf::do_flush()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:269:11: error: ‘char* __streambuf::_pbase’ is inaccessible
     char* _pbase; /* Start of put area. */
           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:468:38: error: within this context
     int do_flush() { return do_write(_pbase, _pptr-_pbase); }
                                      ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:270:11: error: ‘char* __streambuf::_pptr’ is inaccessible
     char* _pptr; /* Current put pointer. */
           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:468:46: error: within this context
     int do_flush() { return do_write(_pbase, _pptr-_pbase); }
                                              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:269:11: error: ‘char* __streambuf::_pbase’ is inaccessible
     char* _pbase; /* Start of put area. */
           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:468:52: error: within this context
     int do_flush() { return do_write(_pbase, _pptr-_pbase); }
                                                    ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In constructor ‘ios::ios(streambuf*, ostream*)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:479:37: error: ‘_fill’ was not declared in this scope
   _strbuf=sb; _tie = tie; _width=0; _fill=' ';
                                     ^
In file included from First.cpp:1:0:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:67:35: error: ‘streamsize’ has not been declared
     ostream& write(const char *s, streamsize n);
                                   ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:68:44: error: ‘streamsize’ has not been declared
     ostream& write(const unsigned char *s, streamsize n)
                                            ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:70:42: error: ‘streamsize’ has not been declared
     ostream& write(const signed char *s, streamsize n)
                                          ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:72:35: error: ‘streamsize’ has not been declared
     ostream& write(const void *s, streamsize n)
                                   ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:74:14: error: expected ‘;’ at end of member declaration
     ostream& seekp(streampos);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:75:14: error: expected ‘;’ at end of member declaration
     ostream& seekp(streamoff, _seek_dir);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:75:20: error: redeclaration of ‘ostream& ostream::seekp’
     ostream& seekp(streamoff, _seek_dir);
                    ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:74:29: note: previous declaration ‘ostream& ostream::seekp’
     ostream& seekp(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:75:29: error: expected ‘)’ before ‘,’ token
     ostream& seekp(streamoff, _seek_dir);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:76:5: error: ‘streampos’ does not name a type
     streampos tellp();
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:78:40: error: ‘_IO_va_list’ has not been declared
     ostream& vform(const char *format, _IO_va_list args);
                                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In constructor ‘ostream:ostream()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:49:5: error: uninitialized reference member in ‘class ostream&’ [-fpermissive]
     ostream() { }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:74:29: note: ‘ostream& ostream::seekp’ should be initialized
     ostream& seekp(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int ostream:opfx()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:56:55: error: ‘_IO_flockfile’ was not declared in this scope
  else { if (_tie) _tie->flush(); _IO_flockfile(_strbuf); return 1;} }
                                                       ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘void ostream:osfx()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:57:42: error: ‘_IO_funlockfile’ was not declared in this scope
     void osfx() { _IO_funlockfile(_strbuf);
                                          ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:121:5: error: ‘_IO_size_t’ does not name a type
     _IO_size_t _gcount;
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:140:30: error: ‘streamsize’ has not been declared
     istream& read(char *ptr, streamsize n);
                              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:141:39: error: ‘streamsize’ has not been declared
     istream& read(unsigned char *ptr, streamsize n)
                                       ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:143:37: error: ‘streamsizepfxe’ has not been declared
     istream& read(signed char *ptr, streamsize n)
                                     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:145:30: error: ‘streamsize’ has not been declared
     istream& read(void *ptr, streamsize n)
                              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:192:5: error: ‘_IO_size_t’ does not name a type
     _IO_size_t gcount() { return _gcount; }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:195:14: error: expected ‘;’ at end of member declaration
     istream& seekg(streampos);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:196:14: error: expected ‘;’ at end of member declaration
     istream& seekg(streamoff, _seek_dir);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:196:20: error: redeclaration of ‘istream& istream::seekg’
     istream& seekg(streamoff, _seek_dir);
                    ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:195:29: note: previous declaration ‘istream& istream::seekg’
     istream& seekg(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:196:29: error: expected ‘)’ before ‘,’ token
     istream& seekg(streamoff, _seek_dir);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:197:5: error: ‘streampos’ does not name a type
     streampos tellg();
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:205:40: error: ‘_IO_va_list’ has not been declared
     istream& vscan(const char *format, _IO_va_list args);
                                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In constructor ‘istream::istream()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:125:16: error: class ‘istream’ does not have any field named ‘_gcount’
     istream(): _gcount (0) { }
                ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:125:5: error: uninitialized reference member in ‘class istream&’ [-fpermissive]
     istream(): _gcount (0) { }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:195:29: note: ‘istream& istream::seekg’ should be initialized
     istream& seekg(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int istream::ipfx(int)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:155:25: error: ‘_IO_flockfile’ was not declared in this scope
    _IO_flockfile(_strbuf);
                         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int istream::ipfx0()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:167:25: error: ‘_IO_flockfile’ was not declared in this scope
    _IO_flockfile(_strbuf);
                         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int istream::ipfx1()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:179:25: error: ‘_IO_flockfile’ was not declared in this scope
    _IO_flockfile(_strbuf);
                         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘void istream::isfx()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:184:42: error: ‘_IO_funlockfile’ was not declared in this scope
     void isfx() { _IO_funlockfile(_strbuf); }
                                          ^
First.cpp: In function ‘int main()’:
First.cpp:5:2: error: ‘reutrn’ was not declared in this scope
  reutrn 0;
  ^
aryadev_chavali@UbuntuProgramming:~/Documents/Programming/C++$ gcc First.cpp -o my.test
In file included from /usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:31:0,
                 from First.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:53:9: error: ‘_G_off_t’ does not name a type
 typedef _G_off_t streamoff;
         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:54:9: error: ‘_G_off_t’ does not name a type
 typedef _G_off_t streampos; // Should perhaps be _G_fpos_t ?
         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:64:5: error: ‘_G_wchar_t’ does not name a type
     _G_wchar_t _fill;
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:144:5: error: ‘_G_wchar_t’ does not name a type
     _G_wchar_t fill() const { return (_G_wchar_t)_fill; }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:145:5: error: ‘_G_wchar_t’ does not name a type
     _G_wchar_t fill(_G_wchar_t newf)
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:249:5: error: ‘streampos’ does not name a type
     streampos _spos; // -2: means that _pos is valid.
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:250:24: error: ‘streampos’ has not been declared
     void set_streampos(streampos sp) { _spos = sp; }
                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘void streammarker::set_streampos(int)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:250:40: error: ‘_spos’ was not declared in this scope
     void set_streampos(streampos sp) { _spos = sp; }
                                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘void streammarker::set_offset(int)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:251:50: error: ‘_spos’ was not declared in this scope
     void set_offset(int offset) { _pos = offset; _spos = (streampos)(-2); }
                                                  ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:251:59: error: ‘streampos’ was not declared in this scope
     void set_offset(int offset) { _pos = offset; _spos = (streampos)(-2); }
                                                           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘int streammarker::saving()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:258:28: error: ‘_spos’ was not declared in this scope
     int saving() { return  _spos == -2; }
                            ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:357:13: error: ‘streampos’ does not name a type
     virtual streampos seekoff(streamoff, _seek_dir, int mode=ios::in|ios::out);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:358:13: error: ‘streampos’ does not name a type
     virtual streampos seekpos(streampos pos, int mode = ios::in|ios::out);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:388:30: error: ‘_G_size_t’ has not been declared
     long sgetline(char* buf, _G_size_t n, char delim, int putback_delim);
                              ^
In file included from /usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:25:0,
                 from /usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:31,
                 from First.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:402:33: error: ‘__gnuc_va_list’ has not been declared
     int vscan(char const *fmt0, _G_va_list ap, ios* stream = NULL);
                                 ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:404:33: error: ‘__gnuc_va_list’ has not been declared
     int vform(char const *fmt0, _G_va_list ap);
                                 ^
In file included from /usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:31:0,
                 from First.cpp:1:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:456:13: error: ‘streampos’ does not name a type
     virtual streampos seekoff(streamoff, _seek_dir, int mode=ios::in|ios::out);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:470:13: error: ‘_G_ssize_t’ does not name a type
     virtual _G_ssize_t sys_read(char* buf, _G_size_t size);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:472:13: error: ‘_G_ssize_t’ does not name a type
     virtual _G_ssize_t sys_write(const void*, long);
             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In member function ‘int filebuf::do_flush()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:269:11: error: ‘char* __streambuf::_pbase’ is inaccessible
     char* _pbase; /* Start of put area. */
           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:468:38: error: within this context
     int do_flush() { return do_write(_pbase, _pptr-_pbase); }
                                      ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:270:11: error: ‘char* __streambuf::_pptr’ is inaccessible
     char* _pptr; /* Current put pointer. */
           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:468:46: error: within this context
     int do_flush() { return do_write(_pbase, _pptr-_pbase); }
                                              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:269:11: error: ‘char* __streambuf::_pbase’ is inaccessible
     char* _pbase; /* Start of put area. */
           ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:468:52: error: within this context
     int do_flush() { return do_write(_pbase, _pptr-_pbase); }
                                                    ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h: In constructor ‘ios::ios(streambuf*, ostream*)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/streambuf.h:479:37: error: ‘_fill’ was not declared in this scope
   _strbuf=sb; _tie = tie; _width=0; _fill=' ';
                                     ^
In file included from First.cpp:1:0:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:67:35: error: ‘streamsize’ has not been declared
     ostream& write(const char *s, streamsize n);
                                   ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:68:44: error: ‘streamsize’ has not been declared
     ostream& write(const unsigned char *s, streamsize n)
                                            ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:70:42: error: ‘streamsize’ has not been declared
     ostream& write(const signed char *s, streamsize n)
                                          ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:72:35: error: ‘streamsize’ has not been declared
     ostream& write(const void *s, streamsize n)
                                   ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:74:14: error: expected ‘;’ at end of member declaration
     ostream& seekp(streampos);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:75:14: error: expected ‘;’ at end of member declaration
     ostream& seekp(streamoff, _seek_dir);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:75:20: error: redeclaration of ‘ostream& ostream::seekp’
     ostream& seekp(streamoff, _seek_dir);
                    ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:74:29: note: previous declaration ‘ostream& ostream::seekp’
     ostream& seekp(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:75:29: error: expected ‘)’ before ‘,’ token
     ostream& seekp(streamoff, _seek_dir);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:76:5: error: ‘streampos’ does not name a type
     streampos tellp();
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:78:40: error: ‘_IO_va_list’ has not been declared
     ostream& vform(const char *format, _IO_va_list args);
                                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In constructor ‘ostream::ostream()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:49:5: error: uninitialized reference member in ‘class ostream&’ [-fpermissive]
     ostream() { }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:74:29: note: ‘ostream& ostream::seekp’ should be initialized
     ostream& seekp(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int ostream::opfx()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:56:55: error: ‘_IO_flockfile’ was not declared in this scope
  else { if (_tie) _tie->flush(); _IO_flockfile(_strbuf); return 1;} }
                                                       ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘void ostream::osfx()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:57:42: error: ‘_IO_funlockfile’ was not declared in this scope
     void osfx() { _IO_funlockfile(_strbuf);
                                          ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: At global scope:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:121:5: error: ‘_IO_size_t’ does not name a type
     _IO_size_t _gcount;
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:140:30: error: ‘streamsize’ has not been declared
     istream& read(char *ptr, streamsize n);
                              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:141:39: error: ‘streamsize’ has not been declared
     istream& read(unsigned char *ptr, streamsize n)
                                       ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:143:37: error: ‘streamsize’ has not been declared
     istream& read(signed char *ptr, streamsize n)
                                     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:145:30: error: ‘streamsize’ has not been declared
     istream& read(void *ptr, streamsize n)
                              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:192:5: error: ‘_IO_size_t’ does not name a type
     _IO_size_t gcount() { return _gcount; }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:195:14: error: expected ‘;’ at end of member declaration
     istream& seekg(streampos);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:196:14: error: expected ‘;’ at end of member declaration
     istream& seekg(streamoff, _seek_dir);
              ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:196:20: error: redeclaration of ‘istream& istream::seekg’
     istream& seekg(streamoff, _seek_dir);
                    ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:195:29: note: previous declaration ‘istream& istream::seekg’
     istream& seekg(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:196:29: error: expected ‘)’ before ‘,’ token
     istream& seekg(streamoff, _seek_dir);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:197:5: error: ‘streampos’ does not name a type
     streampos tellg();
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:205:40: error: ‘_IO_va_list’ has not been declared
     istream& vscan(const char *format, _IO_va_list args);
                                        ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In constructor ‘istream::istream()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:125:16: error: class ‘istream’ does not have any field named ‘_gcount’
     istream(): _gcount (0) { }
                ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:125:5: error: uninitialized reference member in ‘class istream&’ [-fpermissive]
     istream(): _gcount (0) { }
     ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:195:29: note: ‘istream& istream::seekg’ should be initialized
     istream& seekg(streampos);
                             ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int istream::ipfx(int)’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:155:25: error: ‘_IO_flockfile’ was not declared in this scope
    _IO_flockfile(_strbuf);
                         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int istream::ipfx0()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:167:25: error: ‘_IO_flockfile’ was not declared in this scope
    _IO_flockfile(_strbuf);
                         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘int istream::ipfx1()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:179:25: error: ‘_IO_flockfile’ was not declared in this scope
    _IO_flockfile(_strbuf);
                         ^
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h: In member function ‘void istream::isfx()’:
/usr/lib/gcc/x86_64-linux-gnu/5/include/iostream.h:184:42: error: ‘_IO_funlockfile’ was not declared in this scope
     void isfx() { _IO_funlockfile(_strbuf); }


```

---

### Post by kpatz on 2016-11-04
Install build-essential:```
sudo apt-get install build-essential
```Remove the .h from the include:```
#include <iostream>
```You'll also need to add one of these in order to find cout:```
using std::cout;
```or```
using namespace std;
```Once you do these things the code should compile and run.

---

### Post by jerome1232 on 2016-11-04
It's your syntax I think

```
#include <iostream>
using namespace std;
main()
{
    cout << "Hello World \n";
    return 0;
}
```

then try to g++ it

---

### Post by TheFu on 2016-11-04
A little history ... 

The original code was written for an older version "standard" of C++ than commonly used today.  You'll want to be careful about that and follow a specific standard that you want to learn.

For example, your code looks like what I would have written in 1994 in a beginning C++ class.  When the std template library became available and stable in the late 1990s, things started changing.  I think by about 2005-ish (my guess only), most C++ people had switched to the newer standard using namespaces and STL.  I should also point out that pretty much nobody writing production code will use cout/cin.  These don't do enough error prevention to be trusted. Still, handling streams is a handy thing to learn for many interesting purposes - even if not used for console input/output. We all start with this method and I might use cout for a toy program I put together quickly.

---

### Post by spjackson on 2016-11-04
> 
```

#include <iostream.h>
main()

```

If you are trying to learn from a resource that has iostream.h then I strongly recommend that you get hold of something more modern. That form predates the 1998 C++ standard and is therefore far too out of date to be learning today.

As for the 2nd line, I am fairly confident that implicit return types have never been valid C++.

---

### Post by hakuryuu2 on 2016-11-04
Hello! Thank you very much, your solution worked perfectly for me! Please answer another one of my questions if you don't mind, which is: why do we have to declare that we are using namespace std? What does it do? Thanks in advance

---

