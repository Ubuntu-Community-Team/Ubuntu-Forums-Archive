---
title: "Compiling NICOLE doesn't work..."
date: 2008-07-06
forum: Programming Talk
---

### Post by smartboyathome on 2008-07-06
I didn't know where I should post this, so I thought here would be the best place. I am trying to install the program NICOLE (see [here]("http://sourceforge.net/projects/nicole/")), but I can't get it to compile. Since it is no longer maintained, I am going to have to make this compile myself. When I try to run make, I get this:

```
log.cpp: In constructor ‘Log::Log(std::string)’:
log.cpp:36: error: no matching function for call to ‘std::basic_ofstream<char, std::char_traits<char> >::open(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, const std::_Ios_Openmode&)’
/usr/include/c++/4.2/fstream:648: note: candidates are: void std::basic_ofstream<_CharT, _Traits>::open(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]
make[1]: *** [log.o] Error 1
```

Can someone tell me what is wrong with the compile code? Thanks.

---

### Post by LaRoza on 2008-07-06
> **smartboyathome said:**
> I didn't know where I should post this, so I thought here would be the best place. I am trying to install the program NICOLE (see [here]("http://sourceforge.net/projects/nicole/")), but I can't get it to compile. Since it is no longer maintained, I am going to have to make this compile myself. When I try to run make, I get this:

Can someone tell me what is wrong with the compile code? Thanks.

Do you have all the libraries installed (including the mysql libs) needed? Did you configure?

---

### Post by smartboyathome on 2008-07-06
I did configure, and it checked out with all the libraries installed.

---

### Post by haTem on 2008-07-08
Try changing

[PHP]Log::Log ( string fname )
{

	logfile.open ( fname.begin (  ), ios::app );
}[/PHP]

to

[PHP]Log::Log ( string fname )
{

	logfile.open ( fname.c_str (  ), ios::app );
}[/PHP]

I don't have the mysql libs installed, so I can't compile to see if that works. Give it a try and let me know how it goes.

---

