---
title: "Simple ofstream error"
date: 2007-01-07
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-07
I get:
```

~/Desktop$ g++-4.1 class.cc `pkg-config gtkmm-2.4 --cflags --libs`
class.cc: In member function &#32;&#145;virtual void class::save_clicked()&#41;&#146;:
class.cc:218: error: no matching function for call to &#32;&#145;std::basic_ofstream<char, std::char_traits<char> >::basic_ofstream(Glib::ustring&)&#41;&#146;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/fstream:572: note: candidates are: std::basic_ofstream<_CharT, _Traits>::basic_ofstream(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/fstream:556: note:                 std::basic_ofstream<_CharT, _Traits>::basic_ofstream() [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/iosfwd:92: note:                 std::basic_ofstream<char, std::char_traits<char> >::basic_ofstream(const std::basic_ofstream<char, std::char_traits<char> >&)

```
Here is my code:
```

void class::save_clicked() {
	if(file_to_save == "") {
		class::save_as_clicked();
	} else{
		ofstream save_file(file_to_save);
		save_file << text_view.get_buffer()->get_text();
	}

}

```

---

### Post by hod139 on 2007-01-07
I'm guess file_to_save is a std::string.  The argument to save_file has to be char * I think.  Use the function c_str to convert it for you.

```

ofstream save_file(file_to_save.c_str());

```

---

### Post by Ben Sprinkle on 2007-01-07
It was a ustring, thanks for the help. :)

---

