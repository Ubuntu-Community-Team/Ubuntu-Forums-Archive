---
title: "[C++] wxComboBox - Is there a better way?"
date: 2009-05-12
forum: Programming Talk
---

### Post by dodle on 2009-05-12
I was just wondering if there was a better way to do this, or if this is satisfactory:

[php]  wxString sect_opt[] = {_T("Base System"), _T("Communication"), _T("Cross Platform"), _T("Development"),
  		_T("Documentation"), _T("Editors"), _T("Electronics"), _T("Email"), _T("Embedded Devices"),
  		_T("Gnome Desktop Environment"), _T("Games and Amusement"), _T("Graphics"),
  		_T("Internationalization and Localization"), _T("Interpreted Computer Languages"),
  		_T("KDE Desktop Environment"), _T("Libraries"), _T("Libraries - Development"),
  		_T("Libraries - Old"), _T("Mathematics"), _T("Meta Packages"), _T("Miscellaneous - Graphical"),
  		_T("Miscellaneous - Text Based"), _T("Multimedia"), _T("Networking"), _T("Newsgroup"),
  		_T("Perl Programming Language"), _T("Python Programming Language"),
  		_T("Science"), _T("Shells"), _T("System Administration"), _T("TeX Authoring"), _T("Unknown"),
  		_T("Utilities"), _T("Word Processing"), _T("World Wide Web")};


  wxComboBox *sect_widg = new wxComboBox(page_1, -1, sect_opt[31], wxDefaultPosition, wxDefaultSize, 35, sect_opt);
[/php]

---

### Post by dodle on 2009-05-12
I learned this over at [http://wxforum.shadonet.com](http://wxforum.shadonet.com):

[php]wxComboBox *sect_widg = new wxComboBox(page_1, -1, sect_opt[31], wxDefaultPosition,
                                        wxDefaultSize, WXSIZEOF(sect_opt), sect_opt);
[/php]

The WXSIZEOF() option returns the number of items in the array.  Are arrays mutable, or do I need to use something else if I want to add/remove elements?

---

