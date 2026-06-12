---
title: "Why is it so slow?"
date: 2010-08-28
forum: Programming Talk
---

### Post by kahumba on 2010-08-28
Hi,
I'm simply wondering why is this implementation like 400 times slower than that in glib:
Glib::Regex::split_simple("\n", text);

```

std::vector<Glib::ustring>* mySplit(const Glib::ustring& text) {
    std::vector<Glib::ustring>* v = new std::vector<Glib::ustring>();
    static const Glib::ustring ch = "\n";
    int index = text.find(ch);
    int num1 = 0;
    while(index != Glib::ustring::npos) {
        Glib::ustring line = text.substr(num1, index-num1);
        v->push_back(line);
        num1 = index+1;
        index = text.find(ch, num1);
    }

    if(num1 < text.size()) {
        v->push_back(text.substr(num1, text.size()-num1));
    }
    return v;
}

```

PS: to test it I used the file /usr/share/applications/desktop.en_US.utf8.cache

---

