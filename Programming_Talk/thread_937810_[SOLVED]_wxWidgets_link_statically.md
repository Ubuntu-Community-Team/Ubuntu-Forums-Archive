---
title: "[SOLVED] wxWidgets link statically?"
date: 2008-10-04
forum: Programming Talk
---

### Post by WitchCraft on 2008-10-04
Question:

I've installed wxWidgets from the repository.

I wrote a little sample program, and it works well.

Now, the default for wxWidgets is dynamic linking:
# dynamically linked
# g++ -Wall -o ExecutableName source.cpp `wx-config --version=2.8 --libs` `wx-config --version=2.8 --cxxflags` 


Now I wanted to have my application statically linked. I searched via google and looked up the man pages, and saw that it should be possible with:
# statically linked
g++ -Wall -o ExecutableName source.cpp `wx-config --version=2.8 **--static yes** --libs` `wx-config --version=2.8 **--static yes** --cxxflags` 

Now I get the following error message when compiling:
```

./compile-posix.sh

  Warning: No config found to match: /usr/bin/wx-config --version=2.8 --static yes --libs
           in /usr/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.


  Warning: No config found to match: /usr/bin/wx-config --version=2.8 --static yes --cxxflags
           in /usr/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

source.cpp:1:23: error: wx/wxprec.h: No such file or directory
source.cpp:4:20: error: wx/wx.h: No such file or directory
In file included from source.cpp:7:
source.hpp:2:25: error: wx/aboutdlg.h: No such file or directory
source.hpp:3:21: error: wx/menu.h: No such file or directory
source.hpp:4:52: error: wx/process.h: No such file or directory
source.hpp:5:33: error: wx/splash.h: No such file or directory
source.hpp:6:73: error: wx/stdpaths.h: No such file or directory
source.hpp:7:62: error: wx/mstream.h: No such file or directory
source.hpp:8:47: error: wx/socket.h: No such file or directory
source.hpp:9:29: error: wx/string.h: No such file or directory
source.hpp:10:28: error: wx/textctrl.h: No such file or directory
source.hpp:11:54: error: wx/utils.h: No such file or directory
In file included from source.hpp:22,
                 from source.cpp:7:
os_specific.hpp: In function ‘void init_SharedLibraryName()’:
os_specific.hpp:64: error: ‘wxT’ was not declared in this scope
In file included from source.hpp:23,
                 from source.cpp:7:
nonstdlibsubs.hpp: In function ‘std::wstring GetCurrentWorkingDirectory()’:
nonstdlibsubs.hpp:29: error: ‘wxString’ was not declared in this scope
nonstdlibsubs.hpp:29: error: expected `;' before ‘wxstrCurrentWorkingDirectory’
nonstdlibsubs.hpp:30: error: ‘wxstrCurrentWorkingDirectory’ was not declared in this scope
nonstdlibsubs.hpp:32: error: ‘wxT’ was not declared in this scope
nonstdlibsubs.hpp: In function ‘std::wstring ASCII2Unicode(std::string)’:
nonstdlibsubs.hpp:60: error: ‘wxT’ was not declared in this scope
nonstdlibsubs.hpp:64: error: ‘wxT’ was not declared in this scope
nonstdlibsubs.hpp: In function ‘void ProcSplitString(const std::wstring&, std::wstring&, std::wstring&)’:
nonstdlibsubs.hpp:74: error: ‘wxT’ was not declared in this scope
In file included from source.cpp:7:
source.hpp: At global scope:
source.hpp:35: error: expected class-name before ‘{’ token
source.hpp:43: error: expected class-name before ‘{’ token
source.hpp:45: error: expected ‘,’ or ‘...’ before ‘&’ token
source.hpp:45: error: ISO C++ forbids declaration of ‘wxString’ with no type
source.hpp:48: error: expected ‘,’ or ‘...’ before ‘&’ token
source.hpp:48: error: ISO C++ forbids declaration of ‘wxString’ with no type
source.hpp:50: error: ‘wxCommandEvent’ has not been declared
source.hpp:51: error: ‘wxCommandEvent’ has not been declared
source.hpp:51: error: expected ‘,’ or ‘...’ before ‘(’ token
source.hpp:52: error: ‘wxCommandEvent’ has not been declared
source.hpp:53: error: ‘wxCommandEvent’ has not been declared
source.hpp:54: error: ‘wxCommandEvent’ has not been declared
source.hpp:56: error: ISO C++ forbids declaration of ‘wxTextCtrl’ with no type
source.hpp:56: error: expected ‘;’ before ‘*’ token
source.hpp:57: error: ISO C++ forbids declaration of ‘wxMenuBar’ with no type
source.hpp:57: error: expected ‘;’ before ‘*’ token
source.hpp:59: error: ISO C++ forbids declaration of ‘DECLARE_EVENT_TABLE’ with no type
source.hpp:60: error: expected ‘;’ before ‘}’ token
source.hpp:60: error: expected `;' before ‘}’ token
source.hpp:66: error: ‘wxID_HIGHEST’ was not declared in this scope
source.hpp:75: error: ‘wxFrame’ has not been declared
source.hpp:76: error: expected constructor, destructor, or type conversion before ‘EVT_MENU’
hsplash_image.h:1: warning: ‘splash_image_600x480_jpg’ defined but not used

```

Does that mean I need to download, compile and install wxWidgets manually if I want to link it statically, or is there something on the repos, or did i just do something wrong?

---

### Post by nvteighen on 2008-10-04
Just a question, shouldn't be **--static=yes**? You wrote **--static yes**, but all other options use the '='...

Have you the wx2.8-headers package installed? (hell, why don't they use the standard "*-dev" notation?)

But, if you have done everything right, search for a corresponding .a file (static library) for WxWidgets. Otherwise, you'll have to compile WxWidgets into one and that might be tough.

---

### Post by WitchCraft on 2008-10-04
> **nvteighen said:**
> Just a question, shouldn't be **--static=yes**? You wrote **--static yes**, but all other options use the '='...

Have you the wx2.8-headers package installed? (hell, why don't they use the standard "*-dev" notation?)

But, if you have done everything right, search for a corresponding .a file (static library) for WxWidgets. Otherwise, you'll have to compile WxWidgets into one and that might be tough.

yes, you're right, there should be a = in between, but the error remains...

Yes, the wx2.8-headers are installed (wouldn't compile with dynamic linking if I hadn't installed them)

```

g++ -Wall -o executable soure.cpp `wx-config --version=2.8 --static=yes --libs` `wx-config --version=2.8 --static=yes --cxxflags` 

  Warning: No config found to match: /usr/bin/wx-config --version=2.8 --static=yes --libs
           in /usr/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.


  Warning: No config found to match: /usr/bin/wx-config --version=2.8 --static=yes --cxxflags
           in /usr/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

source.cpp:1:23: error: wx/wxprec.h: No such file or directory
source.cpp:4:20: error: wx/wx.h: No such file or directory
In file included from source.cpp:7:
source.hpp:2:25: error: wx/aboutdlg.h: No such file or directory
source.hpp:3:21: error: wx/menu.h: No such file or directory
source.hpp:4:52: error: wx/process.h: No such file or directory
source.hpp:5:33: error: wx/splash.h: No such file or directory
source.hpp:6:73: error: wx/stdpaths.h: No such file or directory
source.hpp:7:62: error: wx/mstream.h: No such file or directory
source.hpp:8:47: error: wx/socket.h: No such file or directory
source.hpp:9:29: error: wx/string.h: No such file or directory
source.hpp:10:28: error: wx/textctrl.h: No such file or directory
source.hpp:11:54: error: wx/utils.h: No such file or directory
In file included from source.hpp:22,
                 from source.cpp:7:
os_specific.hpp: In function ‘void init_SharedLibraryName()’:
os_specific.hpp:64: error: ‘wxT’ was not declared in this scope
In file included from source.hpp:23,
                 from source.cpp:7:
nonstdlibsubs.hpp: In function ‘std::wstring GetCurrentWorkingDirectory()’:
nonstdlibsubs.hpp:29: error: ‘wxString’ was not declared in this scope
nonstdlibsubs.hpp:29: error: expected `;' before ‘wxstrCurrentWorkingDirectory’
nonstdlibsubs.hpp:30: error: ‘wxstrCurrentWorkingDirectory’ was not declared in this scope
nonstdlibsubs.hpp:32: error: ‘wxT’ was not declared in this scope
nonstdlibsubs.hpp: In function ‘std::wstring ASCII2Unicode(std::string)’:
nonstdlibsubs.hpp:60: error: ‘wxT’ was not declared in this scope
nonstdlibsubs.hpp:64: error: ‘wxT’ was not declared in this scope
nonstdlibsubs.hpp: In function ‘void ProcSplitString(const std::wstring&, std::wstring&, std::wstring&)’:
nonstdlibsubs.hpp:74: error: ‘wxT’ was not declared in this scope
In file included from source.cpp:7:
source.hpp: At global scope:
source.hpp:35: error: expected class-name before ‘{’ token
source.hpp:43: error: expected class-name before ‘{’ token
source.hpp:45: error: expected ‘,’ or ‘...’ before ‘&’ token
source.hpp:45: error: ISO C++ forbids declaration of ‘wxString’ with no type
source.hpp:48: error: expected ‘,’ or ‘...’ before ‘&’ token
source.hpp:48: error: ISO C++ forbids declaration of ‘wxString’ with no type
source.hpp:50: error: ‘wxCommandEvent’ has not been declared
source.hpp:51: error: ‘wxCommandEvent’ has not been declared
source.hpp:51: error: expected ‘,’ or ‘...’ before ‘(’ token
source.hpp:52: error: ‘wxCommandEvent’ has not been declared
source.hpp:53: error: ‘wxCommandEvent’ has not been declared
source.hpp:54: error: ‘wxCommandEvent’ has not been declared
source.hpp:56: error: ISO C++ forbids declaration of ‘wxTextCtrl’ with no type
source.hpp:56: error: expected ‘;’ before ‘*’ token
source.hpp:57: error: ISO C++ forbids declaration of ‘wxMenuBar’ with no type
source.hpp:57: error: expected ‘;’ before ‘*’ token
source.hpp:59: error: ISO C++ forbids declaration of ‘DECLARE_EVENT_TABLE’ with no type
source.hpp:60: error: expected ‘;’ before ‘}’ token
source.hpp:60: error: expected `;' before ‘}’ token
source.hpp:66: error: ‘wxID_HIGHEST’ was not declared in this scope
source.hpp:75: error: ‘wxFrame’ has not been declared
source.hpp:76: error: expected constructor, destructor, or type conversion before ‘EVT_MENU’
splash_image.h:1: warning: ‘splash_image_600x480_jpg’ defined but not used

```

---

### Post by SledgeHammer_999 on 2008-10-04
You have to compile wxWidgets for static linkage. There's an option in the "configure" file. As far as I know there is no static version in the repos. You have to build it yourself(just a simple switch in the configure) for the --static=yes to work.

---

### Post by nvteighen on 2008-10-04
I've installed WxWidgets and had a look. The "--script" argument is implemented at wx-config, but I just can't find any static library (.a) but only shared. I smell some Ubuntu-specific thing here.

Using --static=yes on the --cxxflags is irrelevant (this also goes if you ever use pkg-config for some other libraries) and that's hardening the solution to the problem. The .h errors clearly have to do with the way the error (not any static lib available) is handled: wx-config just dies leaving g++ without any proper information and therefre you get preprocessor errors and not linker ones, which would make more sense.

Please, show the output for:
```

g++ -Wall -o executable source.cpp `wx-config --version=2.8 --static=yes --libs` `wx-config --version=2.8 --cxxflags`

```

---

### Post by WitchCraft on 2008-10-04
> **nvteighen said:**
> I've installed WxWidgets and had a look. The "--script" argument is implemented at wx-config, but I just can't find any static library (.a) but only shared. I smell some Ubuntu-specific thing here.

Using --static=yes on the --cxxflags is irrelevant (this also goes if you ever use pkg-config for some other libraries) and that's hardening the solution to the problem. The .h errors clearly have to do with the way the error (not any static lib available) is handled: wx-config just dies leaving g++ without any proper information and therefre you get preprocessor errors and not linker ones, which would make more sense.

Please, show the output for:
```

g++ -Wall -o executable source.cpp `wx-config --version=2.8 --static=yes --libs` `wx-config --version=2.8 --cxxflags`

```

That's the output:
```


  Warning: No config found to match: /usr/bin/wx-config --version=2.8 --static=yes --libs
           in /usr/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

/tmp/ccV3wCsk.o: In function `__static_initialization_and_destruction_0(int, int)':
source.cpp:(.text+0x2351): undefined reference to `wxEventHashTable::wxEventHashTable(wxEventTable const&)'
source.cpp:(.text+0x2356): undefined reference to `wxEventHashTable::~wxEventHashTable()'
source.cpp:(.text+0x23b3): undefined reference to `wxEVT_COMMAND_MENU_SELECTED'
source.cpp:(.text+0x23ff): undefined reference to `wxEVT_COMMAND_MENU_SELECTED'
source.cpp:(.text+0x244b): undefined reference to `wxEVT_COMMAND_MENU_SELECTED'
source.cpp:(.text+0x2497): undefined reference to `wxEVT_COMMAND_MENU_SELECTED'
source.cpp:(.text+0x24e3): undefined reference to `wxEVT_COMMAND_MENU_SELECTED'
source.cpp:(.text+0x252e): undefined reference to `wxEVT_NULL'
/tmp/ccV3wCsk.o: In function `MainFrame::OnQuit(wxCommandEvent&)':
source.cpp:(.text+0x2589): undefined reference to `wxWindowBase::Close(bool)'
/tmp/ccV3wCsk.o: In function `MainFrame::OnAbout(wxCommandEvent&)':
source.cpp:(.text+0x2923): undefined reference to `wxEmptyString'
source.cpp:(.text+0x29d6): undefined reference to `wxEmptyString'
source.cpp:(.text+0x2d10): undefined reference to `wxAboutBox(wxAboutDialogInfo const&)'
/tmp/ccV3wCsk.o: In function `MainFrame::OnHelp(wxCommandEvent&)':
source.cpp:(.text+0x2e83): undefined reference to `wxLaunchDefaultBrowser(wxString const&, int)'
/tmp/ccV3wCsk.o: In function `MainFrame::DoAsyncExec(wxString const&)':
source.cpp:(.text+0x2f3a): undefined reference to `wxExecute(wxString const&, int, wxProcess*)'
/tmp/ccV3wCsk.o: In function `MainFrame::OnAsyncExec(wxCommandEvent&)':
source.cpp:(.text+0x3083): undefined reference to `wxGetTextFromUser(wxString const&, wxString const&, wxString const&, wxWindow*, int, int, bool)'
/tmp/ccV3wCsk.o: In function `main':
source.cpp:(.text+0x31a1): undefined reference to `wxEntry(int&, char**)'
/tmp/ccV3wCsk.o: In function `wxCreateApp()':
source.cpp:(.text+0x31c6): undefined reference to `wxAppConsole::CheckBuildOptions(char const*, char const*)'
/tmp/ccV3wCsk.o: In function `GetCurrentWorkingDirectory()':
source.cpp:(.text+0x386e): undefined reference to `wxStandardPathsBase::Get()'
/tmp/ccV3wCsk.o: In function `ProcExecuteCommand(MainFrame*, std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> > const&)':
source.cpp:(.text+0x41b5): undefined reference to `wxSetWorkingDirectory(wxString const&)'
source.cpp:(.text+0x4242): undefined reference to `wxSetEnv(wxString const&, wchar_t const*)'
source.cpp:(.text+0x430b): undefined reference to `wxSetEnv(wxString const&, wchar_t const*)'
source.cpp:(.text+0x43c4): undefined reference to `wxSleep(int)'
source.cpp:(.text+0x4415): undefined reference to `wxSetWorkingDirectory(wxString const&)'
/tmp/ccV3wCsk.o: In function `MainFrame::MyOpenFile()':
source.cpp:(.text+0x4d03): undefined reference to `wxGetOsDescription()'
source.cpp:(.text+0x4e1b): undefined reference to `wxIsPlatform64Bit()'
source.cpp:(.text+0x4fc8): undefined reference to `wxIsPlatformLittleEndian()'
source.cpp:(.text+0x519d): undefined reference to `wxGetFreeMemory()'
source.cpp:(.text+0x51b8): undefined reference to `wxLongLongNative::ToString() const'
source.cpp:(.text+0x52eb): undefined reference to `wxGetUserName()'
source.cpp:(.text+0x5412): undefined reference to `wxGetUserId()'
source.cpp:(.text+0x552d): undefined reference to `wxGetHomeDir()'
source.cpp:(.text+0x5648): undefined reference to `wxGetHostName()'
source.cpp:(.text+0x5763): undefined reference to `wxGetFullHostName()'
source.cpp:(.text+0x587e): undefined reference to `wxGetEmailAddress()'
source.cpp:(.text+0x58fa): undefined reference to `wxIPV4address::wxIPV4address()'
source.cpp:(.text+0x5961): undefined reference to `wxIPV4address::Hostname(wxString const&)'
source.cpp:(.text+0x598e): undefined reference to `wxIPV4address::Service(unsigned short)'
source.cpp:(.text+0x59de): undefined reference to `wxIPV4address::wxIPV4address()'
source.cpp:(.text+0x59f4): undefined reference to `wxSocketClient::wxSocketClient(int)'
source.cpp:(.text+0x5a22): undefined reference to `wxSocketClient::Connect(wxSockAddress&, bool)'
source.cpp:(.text+0x5a42): undefined reference to `wxSocketBase::GetLocal(wxSockAddress&) const'
source.cpp:(.text+0x5a57): undefined reference to `wxIPV4address::IPAddress() const'
source.cpp:(.text+0x5ac1): undefined reference to `wxIPV4address::wxIPV4address()'
source.cpp:(.text+0x5acc): undefined reference to `wxGetFullHostName()'
source.cpp:(.text+0x5ae4): undefined reference to `wxIPV4address::Hostname(wxString const&)'
source.cpp:(.text+0x5b04): undefined reference to `wxIPV4address::IPAddress() const'
source.cpp:(.text+0x5b68): undefined reference to `wxIPV4address::~wxIPV4address()'
source.cpp:(.text+0x5bc1): undefined reference to `wxIPV4address::~wxIPV4address()'
source.cpp:(.text+0x5cba): undefined reference to `wxEmptyString'
source.cpp:(.text+0x5cd7): undefined reference to `wxEmptyString'
source.cpp:(.text+0x5d13): undefined reference to `wxFileDialogNameStr'
source.cpp:(.text+0x5d4e): undefined reference to `wxDefaultSize'
source.cpp:(.text+0x5d56): undefined reference to `wxDefaultPosition'
source.cpp:(.text+0x5d98): undefined reference to `wxFileDialog::wxFileDialog(wxWindow*, wxString const&, wxString const&, wxString const&, wxString const&, long, wxPoint const&, wxSize const&, wxString const&)'
source.cpp:(.text+0x65ce): undefined reference to `wxSocketClient::~wxSocketClient()'
source.cpp:(.text+0x65f8): undefined reference to `wxSocketClient::~wxSocketClient()'
source.cpp:(.text+0x6606): undefined reference to `wxIPV4address::~wxIPV4address()'
source.cpp:(.text+0x662e): undefined reference to `wxIPV4address::~wxIPV4address()'
source.cpp:(.text+0x664a): undefined reference to `wxIPV4address::~wxIPV4address()'
source.cpp:(.text+0x667e): undefined reference to `wxIPV4address::~wxIPV4address()'
/tmp/ccV3wCsk.o: In function `ProcStartGame(MainFrame*)':
source.cpp:(.text+0x6fdf): undefined reference to `wxWindowBase::Close(bool)'
source.cpp:(.text+0x724c): undefined reference to `wxWindowBase::Close(bool)'
/tmp/ccV3wCsk.o: In function `MainFrame::MainFrame(wxString const&, wxPoint const&, wxSize const&)':
source.cpp:(.text+0x72b1): undefined reference to `wxFrameNameStr'
source.cpp:(.text+0x7326): undefined reference to `wxStatusLineNameStr'
source.cpp:(.text+0x73a6): undefined reference to `wxFrame::CreateStatusBar(int, long, int, wxString const&)'
source.cpp:(.text+0x73dd): undefined reference to `wxMenuBar::wxMenuBar()'
source.cpp:(.text+0x7b5b): undefined reference to `wxFrameBase::SetMenuBar(wxMenuBar*)'
source.cpp:(.text+0x7bc1): undefined reference to `wxTextCtrlNameStr'
source.cpp:(.text+0x7bfc): undefined reference to `wxDefaultValidator'
source.cpp:(.text+0x7c0c): undefined reference to `wxDefaultSize'
source.cpp:(.text+0x7c14): undefined reference to `wxDefaultPosition'
source.cpp:(.text+0x7c38): undefined reference to `wxTextCtrl::wxTextCtrl(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxValidator const&, wxString const&)'
source.cpp:(.text+0x7d6c): undefined reference to `wxImage::AddHandler(wxImageHandler*)'
source.cpp:(.text+0x7dce): undefined reference to `wxMemoryInputStream::wxMemoryInputStream(void const*, unsigned int)'
source.cpp:(.text+0x7e14): undefined reference to `wxImage::LoadFile(wxInputStream&, long, int)'
source.cpp:(.text+0x7e61): undefined reference to `wxDefaultSize'
source.cpp:(.text+0x7e69): undefined reference to `wxDefaultPosition'
source.cpp:(.text+0x7ea1): undefined reference to `wxSplashScreen::wxSplashScreen(wxBitmap const&, long, int, wxWindow*, int, wxPoint const&, wxSize const&, long)'
source.cpp:(.text+0x7ec1): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x7f26): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x7f7a): undefined reference to `wxYield()'
source.cpp:(.text+0x7f86): undefined reference to `wxSleep(int)'
source.cpp:(.text+0x8016): undefined reference to `wxMemoryInputStream::~wxMemoryInputStream()'
source.cpp:(.text+0x803e): undefined reference to `wxMemoryInputStream::~wxMemoryInputStream()'
source.cpp:(.text+0x8057): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x807c): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x80ad): undefined reference to `wxFrame::~wxFrame()'
/tmp/ccV3wCsk.o: In function `MainFrame::MainFrame(wxString const&, wxPoint const&, wxSize const&)':
source.cpp:(.text+0x8211): undefined reference to `wxFrameNameStr'
source.cpp:(.text+0x8286): undefined reference to `wxStatusLineNameStr'
source.cpp:(.text+0x8306): undefined reference to `wxFrame::CreateStatusBar(int, long, int, wxString const&)'
source.cpp:(.text+0x833d): undefined reference to `wxMenuBar::wxMenuBar()'
source.cpp:(.text+0x8abb): undefined reference to `wxFrameBase::SetMenuBar(wxMenuBar*)'
source.cpp:(.text+0x8b21): undefined reference to `wxTextCtrlNameStr'
source.cpp:(.text+0x8b5c): undefined reference to `wxDefaultValidator'
source.cpp:(.text+0x8b6c): undefined reference to `wxDefaultSize'
source.cpp:(.text+0x8b74): undefined reference to `wxDefaultPosition'
source.cpp:(.text+0x8b98): undefined reference to `wxTextCtrl::wxTextCtrl(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxValidator const&, wxString const&)'
source.cpp:(.text+0x8ccc): undefined reference to `wxImage::AddHandler(wxImageHandler*)'
source.cpp:(.text+0x8d2e): undefined reference to `wxMemoryInputStream::wxMemoryInputStream(void const*, unsigned int)'
source.cpp:(.text+0x8d74): undefined reference to `wxImage::LoadFile(wxInputStream&, long, int)'
source.cpp:(.text+0x8dc1): undefined reference to `wxDefaultSize'
source.cpp:(.text+0x8dc9): undefined reference to `wxDefaultPosition'
source.cpp:(.text+0x8e01): undefined reference to `wxSplashScreen::wxSplashScreen(wxBitmap const&, long, int, wxWindow*, int, wxPoint const&, wxSize const&, long)'
source.cpp:(.text+0x8e21): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x8e86): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x8eda): undefined reference to `wxYield()'
source.cpp:(.text+0x8ee6): undefined reference to `wxSleep(int)'
source.cpp:(.text+0x8f76): undefined reference to `wxMemoryInputStream::~wxMemoryInputStream()'
source.cpp:(.text+0x8f9e): undefined reference to `wxMemoryInputStream::~wxMemoryInputStream()'
source.cpp:(.text+0x8fb7): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x8fdc): undefined reference to `wxBitmap::~wxBitmap()'
source.cpp:(.text+0x900d): undefined reference to `wxFrame::~wxFrame()'
/tmp/ccV3wCsk.o: In function `wxStringBase::Init()':
source.cpp:(.text._ZN12wxStringBase4InitEv[wxStringBase::Init()]+0x4): undefined reference to `wxEmptyString'
/tmp/ccV3wCsk.o: In function `wxObject::wxObject()':
source.cpp:(.text._ZN8wxObjectC2Ev[wxObject::wxObject()]+0x8): undefined reference to `vtable for wxObject'
/tmp/ccV3wCsk.o: In function `wxAppConsole::SetInitializerFunction(wxAppConsole* (*)())':
source.cpp:(.text._ZN12wxAppConsole22SetInitializerFunctionEPFPS_vE[wxAppConsole::SetInitializerFunction(wxAppConsole* (*)())]+0x7): undefined reference to `wxAppConsole::ms_appInitFn'
/tmp/ccV3wCsk.o: In function `wxAppConsole::GetInstance()':
source.cpp:(.text._ZN12wxAppConsole11GetInstanceEv[wxAppConsole::GetInstance()]+0x4): undefined reference to `wxAppConsole::ms_appInstance'
/tmp/ccV3wCsk.o: In function `wxGDIObject::wxGDIObject()':
source.cpp:(.text._ZN11wxGDIObjectC2Ev[wxGDIObject::wxGDIObject()]+0x16): undefined reference to `vtable for wxGDIObject'
/tmp/ccV3wCsk.o: In function `wxBitmapBase::wxBitmapBase()':
source.cpp:(.text._ZN12wxBitmapBaseC2Ev[wxBitmapBase::wxBitmapBase()]+0x16): undefined reference to `vtable for wxBitmapBase'
/tmp/ccV3wCsk.o: In function `wxBitmap::wxBitmap()':
source.cpp:(.text._ZN8wxBitmapC1Ev[wxBitmap::wxBitmap()]+0x16): undefined reference to `vtable for wxBitmap'
/tmp/ccV3wCsk.o: In function `wxImage::wxImage()':
source.cpp:(.text._ZN7wxImageC1Ev[wxImage::wxImage()]+0x16): undefined reference to `vtable for wxImage'
/tmp/ccV3wCsk.o:(.rodata+0x2440): undefined reference to `wxFrameBase::sm_eventTable'
/tmp/ccV3wCsk.o: In function `wxThreadHelperThread::~wxThreadHelperThread()':
source.cpp:(.text._ZN20wxThreadHelperThreadD0Ev[wxThreadHelperThread::~wxThreadHelperThread()]+0x16): undefined reference to `wxThread::~wxThread()'
/tmp/ccV3wCsk.o: In function `wxThreadHelperThread::~wxThreadHelperThread()':
source.cpp:(.text._ZN20wxThreadHelperThreadD1Ev[wxThreadHelperThread::~wxThreadHelperThread()]+0x16): undefined reference to `wxThread::~wxThread()'
/tmp/ccV3wCsk.o: In function `wxTransform2D::InverseTransform(wxRect2DInt*) const':
source.cpp:(.text._ZNK13wxTransform2D16InverseTransformEP11wxRect2DInt[wxTransform2D::InverseTransform(wxRect2DInt*) const]+0x89): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
/tmp/ccV3wCsk.o: In function `wxTransform2D::Transform(wxRect2DInt*) const':
source.cpp:(.text._ZNK13wxTransform2D9TransformEP11wxRect2DInt[wxTransform2D::Transform(wxRect2DInt*) const]+0x89): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
/tmp/ccV3wCsk.o: In function `wxWindowBase::SetInitialBestSize(wxSize const&)':
source.cpp:(.text._ZN12wxWindowBase18SetInitialBestSizeERK6wxSize[wxWindowBase::SetInitialBestSize(wxSize const&)]+0x14): undefined reference to `wxWindowBase::SetInitialSize(wxSize const&)'
/tmp/ccV3wCsk.o: In function `wxWindowBase::GetDefaultAttributes() const':
source.cpp:(.text._ZNK12wxWindowBase20GetDefaultAttributesEv[wxWindowBase::GetDefaultAttributes() const]+0x20): undefined reference to `wxWindowBase::GetClassDefaultAttributes(wxWindowVariant)'
/tmp/ccV3wCsk.o: In function `wxWindowBase::HasCapture() const':
source.cpp:(.text._ZNK12wxWindowBase10HasCaptureEv[wxWindowBase::HasCapture() const]+0x7): undefined reference to `wxWindowBase::GetCapture()'
/tmp/ccV3wCsk.o: In function `wxObject::operator=(wxObject const&)':
source.cpp:(.text._ZN8wxObjectaSERKS_[wxObject::operator=(wxObject const&)]+0x1c): undefined reference to `wxObject::Ref(wxObject const&)'
/tmp/ccV3wCsk.o: In function `wxString::operator=(wxString const&)':
source.cpp:(.text._ZN8wxStringaSERKS_[wxString::operator=(wxString const&)]+0x14): undefined reference to `wxStringBase::operator=(wxStringBase const&)'
/tmp/ccV3wCsk.o: In function `wxStringBase::wxStringBase(wchar_t const*)':
source.cpp:(.text._ZN12wxStringBaseC2EPKw[wxStringBase::wxStringBase(wchar_t const*)]+0x7): undefined reference to `wxStringBase::npos'
source.cpp:(.text._ZN12wxStringBaseC2EPKw[wxStringBase::wxStringBase(wchar_t const*)]+0x25): undefined reference to `wxStringBase::InitWith(wchar_t const*, unsigned int, unsigned int)'
/tmp/ccV3wCsk.o: In function `wxWindow::GetLabel() const':
source.cpp:(.text._ZNK8wxWindow8GetLabelEv[wxWindow::GetLabel() const]+0xd): undefined reference to `wxEmptyString'
/tmp/ccV3wCsk.o: In function `MainFrame::~MainFrame()':
source.cpp:(.text._ZN9MainFrameD0Ev[MainFrame::~MainFrame()]+0x16): undefined reference to `wxFrame::~wxFrame()'
/tmp/ccV3wCsk.o: In function `MainFrame::~MainFrame()':
source.cpp:(.text._ZN9MainFrameD1Ev[MainFrame::~MainFrame()]+0x16): undefined reference to `wxFrame::~wxFrame()'
/tmp/ccV3wCsk.o: In function `MainApp::~MainApp()':
source.cpp:(.text._ZN7MainAppD0Ev[MainApp::~MainApp()]+0x16): undefined reference to `wxApp::~wxApp()'
/tmp/ccV3wCsk.o: In function `MainApp::~MainApp()':
source.cpp:(.text._ZN7MainAppD1Ev[MainApp::~MainApp()]+0x16): undefined reference to `wxApp::~wxApp()'
/tmp/ccV3wCsk.o: In function `wxArrayString::wxArrayString()':
source.cpp:(.text._ZN13wxArrayStringC1Ev[wxArrayString::wxArrayString()]+0x15): undefined reference to `wxArrayString::Init(bool)'
/tmp/ccV3wCsk.o: In function `wxIcon::~wxIcon()':
source.cpp:(.text._ZN6wxIconD1Ev[wxIcon::~wxIcon()]+0xb): undefined reference to `vtable for wxIcon'
source.cpp:(.text._ZN6wxIconD1Ev[wxIcon::~wxIcon()]+0x16): undefined reference to `wxBitmap::~wxBitmap()'
/tmp/ccV3wCsk.o: In function `wxArrayString::push_back(wxString const&)':
source.cpp:(.text._ZN13wxArrayString9push_backERK8wxString[wxArrayString::push_back(wxString const&)]+0x1c): undefined reference to `wxArrayString::Add(wxString const&, unsigned int)'
/tmp/ccV3wCsk.o: In function `wxAboutDialogInfo::wxAboutDialogInfo()':
source.cpp:(.text._ZN17wxAboutDialogInfoC1Ev[wxAboutDialogInfo::wxAboutDialogInfo()]+0x55): undefined reference to `wxIcon::wxIcon()'
source.cpp:(.text._ZN17wxAboutDialogInfoC1Ev[wxAboutDialogInfo::wxAboutDialogInfo()]+0xc8): undefined reference to `wxArrayString::~wxArrayString()'
source.cpp:(.text._ZN17wxAboutDialogInfoC1Ev[wxAboutDialogInfo::wxAboutDialogInfo()]+0xea): undefined reference to `wxArrayString::~wxArrayString()'
source.cpp:(.text._ZN17wxAboutDialogInfoC1Ev[wxAboutDialogInfo::wxAboutDialogInfo()]+0x10c): undefined reference to `wxArrayString::~wxArrayString()'
/tmp/ccV3wCsk.o: In function `wxAboutDialogInfo::~wxAboutDialogInfo()':
source.cpp:(.text._ZN17wxAboutDialogInfoD1Ev[wxAboutDialogInfo::~wxAboutDialogInfo()]+0x12): undefined reference to `wxArrayString::~wxArrayString()'
source.cpp:(.text._ZN17wxAboutDialogInfoD1Ev[wxAboutDialogInfo::~wxAboutDialogInfo()]+0x26): undefined reference to `wxArrayString::~wxArrayString()'
/tmp/ccV3wCsk.o:source.cpp:(.text._ZN17wxAboutDialogInfoD1Ev[wxAboutDialogInfo::~wxAboutDialogInfo()]+0x48): more undefined references to `wxArrayString::~wxArrayString()' follow
/tmp/ccV3wCsk.o: In function `wxProcess::wxProcess(wxEvtHandler*, int)':
source.cpp:(.text._ZN9wxProcessC1EP12wxEvtHandleri[wxProcess::wxProcess(wxEvtHandler*, int)]+0xf): undefined reference to `wxEvtHandler::wxEvtHandler()'
source.cpp:(.text._ZN9wxProcessC1EP12wxEvtHandleri[wxProcess::wxProcess(wxEvtHandler*, int)]+0x18): undefined reference to `vtable for wxProcess'
source.cpp:(.text._ZN9wxProcessC1EP12wxEvtHandleri[wxProcess::wxProcess(wxEvtHandler*, int)]+0x39): undefined reference to `wxProcess::Init(wxEvtHandler*, int, int)'
source.cpp:(.text._ZN9wxProcessC1EP12wxEvtHandleri[wxProcess::wxProcess(wxEvtHandler*, int)]+0x4e): undefined reference to `wxEvtHandler::~wxEvtHandler()'
/tmp/ccV3wCsk.o: In function `wxFrame::wxFrame(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxString const&)':
source.cpp:(.text._ZN7wxFrameC2EP8wxWindowiRK8wxStringRK7wxPointRK6wxSizelS4_[wxFrame::wxFrame(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxString const&)]+0xf): undefined reference to `wxFrameBase::wxFrameBase()'
source.cpp:(.text._ZN7wxFrameC2EP8wxWindowiRK8wxStringRK7wxPointRK6wxSizelS4_[wxFrame::wxFrame(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxString const&)]+0x18): undefined reference to `vtable for wxFrame'
source.cpp:(.text._ZN7wxFrameC2EP8wxWindowiRK8wxStringRK7wxPointRK6wxSizelS4_[wxFrame::wxFrame(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxString const&)]+0x23): undefined reference to `wxFrame::Init()'
source.cpp:(.text._ZN7wxFrameC2EP8wxWindowiRK8wxStringRK7wxPointRK6wxSizelS4_[wxFrame::wxFrame(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxString const&)]+0x5f): undefined reference to `wxFrame::Create(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxString const&)'
source.cpp:(.text._ZN7wxFrameC2EP8wxWindowiRK8wxStringRK7wxPointRK6wxSizelS4_[wxFrame::wxFrame(wxWindow*, int, wxString const&, wxPoint const&, wxSize const&, long, wxString const&)]+0x74): undefined reference to `wxFrameBase::~wxFrameBase()'
/tmp/ccV3wCsk.o: In function `wxMenuItemList::Find(wxListKey const&) const':
source.cpp:(.text._ZNK14wxMenuItemList4FindERK9wxListKey[wxMenuItemList::Find(wxListKey const&) const]+0x14): undefined reference to `wxListBase::Find(wxListKey const&) const'
/tmp/ccV3wCsk.o: In function `wxwxMenuItemListNode::wxwxMenuItemListNode(wxListBase*, wxwxMenuItemListNode*, wxwxMenuItemListNode*, wxMenuItem*, wxListKey const&)':
source.cpp:(.text._ZN20wxwxMenuItemListNodeC1EP10wxListBasePS_S2_P10wxMenuItemRK9wxListKey[wxwxMenuItemListNode::wxwxMenuItemListNode(wxListBase*, wxwxMenuItemListNode*, wxwxMenuItemListNode*, wxMenuItem*, wxListKey const&)]+0x31): undefined reference to `wxNodeBase::wxNodeBase(wxListBase*, wxNodeBase*, wxNodeBase*, void*, wxListKey const&)'
source.cpp:(.text._ZN20wxwxMenuItemListNodeC1EP10wxListBasePS_S2_P10wxMenuItemRK9wxListKey[wxwxMenuItemListNode::wxwxMenuItemListNode(wxListBase*, wxwxMenuItemListNode*, wxwxMenuItemListNode*, wxMenuItem*, wxListKey const&)]+0x3a): undefined reference to `vtable for wxwxMenuItemListNode'
/tmp/ccV3wCsk.o: In function `wxMenuItemList::~wxMenuItemList()':
source.cpp:(.text._ZN14wxMenuItemListD0Ev[wxMenuItemList::~wxMenuItemList()]+0x16): undefined reference to `wxListBase::~wxListBase()'
/tmp/ccV3wCsk.o: In function `wxMenuItemList::~wxMenuItemList()':
source.cpp:(.text._ZN14wxMenuItemListD1Ev[wxMenuItemList::~wxMenuItemList()]+0x16): undefined reference to `wxListBase::~wxListBase()'
/tmp/ccV3wCsk.o: In function `wxObject::~wxObject()':
source.cpp:(.text._ZN8wxObjectD2Ev[wxObject::~wxObject()]+0xb): undefined reference to `vtable for wxObject'
source.cpp:(.text._ZN8wxObjectD2Ev[wxObject::~wxObject()]+0x16): undefined reference to `wxObject::UnRef()'
/tmp/ccV3wCsk.o: In function `wxListBase::wxListBase(wxKeyType)':
source.cpp:(.text._ZN10wxListBaseC2E9wxKeyType[wxListBase::wxListBase(wxKeyType)]+0x18): undefined reference to `vtable for wxListBase'
source.cpp:(.text._ZN10wxListBaseC2E9wxKeyType[wxListBase::wxListBase(wxKeyType)]+0x2a): undefined reference to `wxListBase::Init(wxKeyType)'
/tmp/ccV3wCsk.o: In function `wxMenuBase::wxMenuBase(long)':
source.cpp:(.text._ZN10wxMenuBaseC2El[wxMenuBase::wxMenuBase(long)]+0xf): undefined reference to `wxEvtHandler::wxEvtHandler()'
source.cpp:(.text._ZN10wxMenuBaseC2El[wxMenuBase::wxMenuBase(long)]+0x18): undefined reference to `vtable for wxMenuBase'
source.cpp:(.text._ZN10wxMenuBaseC2El[wxMenuBase::wxMenuBase(long)]+0x4e): undefined reference to `wxMenuBase::Init(long)'
source.cpp:(.text._ZN10wxMenuBaseC2El[wxMenuBase::wxMenuBase(long)]+0xa3): undefined reference to `wxEvtHandler::~wxEvtHandler()'
/tmp/ccV3wCsk.o: In function `wxMenu::wxMenu(long)':
source.cpp:(.text._ZN6wxMenuC1El[wxMenu::wxMenu(long)]+0x1f): undefined reference to `vtable for wxMenu'
source.cpp:(.text._ZN6wxMenuC1El[wxMenu::wxMenu(long)]+0x2a): undefined reference to `wxMenu::Init()'
source.cpp:(.text._ZN6wxMenuC1El[wxMenu::wxMenu(long)]+0x3f): undefined reference to `wxMenuBase::~wxMenuBase()'
/tmp/ccV3wCsk.o: In function `wxImageHandler::wxImageHandler()':
source.cpp:(.text._ZN14wxImageHandlerC2Ev[wxImageHandler::wxImageHandler()]+0x18): undefined reference to `vtable for wxImageHandler'
source.cpp:(.text._ZN14wxImageHandlerC2Ev[wxImageHandler::wxImageHandler()]+0x1e): undefined reference to `wxEmptyString'
source.cpp:(.text._ZN14wxImageHandlerC2Ev[wxImageHandler::wxImageHandler()]+0x35): undefined reference to `wxEmptyString'
/tmp/ccV3wCsk.o: In function `wxImageHandler::~wxImageHandler()':
source.cpp:(.text._ZN14wxImageHandlerD2Ev[wxImageHandler::~wxImageHandler()]+0xb): undefined reference to `vtable for wxImageHandler'
/tmp/ccV3wCsk.o: In function `wxGDIObject::~wxGDIObject()':
source.cpp:(.text._ZN11wxGDIObjectD2Ev[wxGDIObject::~wxGDIObject()]+0xb): undefined reference to `vtable for wxGDIObject'
/tmp/ccV3wCsk.o: In function `wxBitmapBase::~wxBitmapBase()':
source.cpp:(.text._ZN12wxBitmapBaseD2Ev[wxBitmapBase::~wxBitmapBase()]+0xb): undefined reference to `vtable for wxBitmapBase'
/tmp/ccV3wCsk.o: In function `wxImage::~wxImage()':
source.cpp:(.text._ZN7wxImageD1Ev[wxImage::~wxImage()]+0xb): undefined reference to `vtable for wxImage'
/tmp/ccV3wCsk.o: In function `wxMenuBase::Append(int, wxString const&, wxString const&, wxItemKind)':
source.cpp:(.text._ZN10wxMenuBase6AppendEiRK8wxStringS2_10wxItemKind[wxMenuBase::Append(int, wxString const&, wxString const&, wxItemKind)]+0x3c): undefined reference to `wxMenuItemBase::New(wxMenu*, int, wxString const&, wxString const&, wxItemKind, wxMenu*)'
/tmp/ccV3wCsk.o: In function `wxMenuBase::AppendSeparator()':
source.cpp:(.text._ZN10wxMenuBase15AppendSeparatorEv[wxMenuBase::AppendSeparator()]+0x9): undefined reference to `wxEmptyString'
source.cpp:(.text._ZN10wxMenuBase15AppendSeparatorEv[wxMenuBase::AppendSeparator()]+0x1d): undefined reference to `wxEmptyString'
/tmp/ccV3wCsk.o: In function `wxString::operator=(wchar_t const*)':
source.cpp:(.text._ZN8wxStringaSEPKw[wxString::operator=(wchar_t const*)]+0x14): undefined reference to `wxStringBase::operator=(wchar_t const*)'
/tmp/ccV3wCsk.o: In function `wxJPEGHandler::wxJPEGHandler()':
source.cpp:(.text._ZN13wxJPEGHandlerC1Ev[wxJPEGHandler::wxJPEGHandler()]+0x18): undefined reference to `vtable for wxJPEGHandler'
/tmp/ccV3wCsk.o: In function `wxBitmap::wxBitmap(wxImage const&, int)':
source.cpp:(.text._ZN8wxBitmapC1ERK7wxImagei[wxBitmap::wxBitmap(wxImage const&, int)]+0x18): undefined reference to `vtable for wxBitmap'
source.cpp:(.text._ZN8wxBitmapC1ERK7wxImagei[wxBitmap::wxBitmap(wxImage const&, int)]+0x31): undefined reference to `wxBitmap::CreateFromImage(wxImage const&, int)'
/tmp/ccV3wCsk.o: In function `MainApp::MainApp()':
source.cpp:(.text._ZN7MainAppC1Ev[MainApp::MainApp()]+0xd): undefined reference to `wxApp::wxApp()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x8): undefined reference to `wxApp::GetClassInfo() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x14): undefined reference to `wxObject::CreateRefData() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x18): undefined reference to `wxObject::CloneRefData(wxObjectRefData const*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x1c): undefined reference to `wxEvtHandler::ProcessEvent(wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x20): undefined reference to `wxEvtHandler::SearchEventTable(wxEventTable&, wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x28): undefined reference to `wxEvtHandler::TryParent(wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x2c): undefined reference to `wxApp::GetEventTable() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x30): undefined reference to `wxApp::GetEventHashTable() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x34): undefined reference to `wxEvtHandler::DoSetClientObject(wxClientData*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x38): undefined reference to `wxEvtHandler::DoGetClientObject() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x3c): undefined reference to `wxEvtHandler::DoSetClientData(void*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x40): undefined reference to `wxEvtHandler::DoGetClientData() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x44): undefined reference to `wxApp::Initialize(int&, wchar_t**)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x50): undefined reference to `wxApp::OnInitGui()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x54): undefined reference to `wxAppBase::OnRun()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x58): undefined reference to `wxAppBase::OnExit()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x5c): undefined reference to `wxApp::CleanUp()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x64): undefined reference to `wxAppBase::Exit()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x68): undefined reference to `wxAppBase::OnInitCmdLine(wxCmdLineParser&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x6c): undefined reference to `wxAppBase::OnCmdLineParsed(wxCmdLineParser&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x70): undefined reference to `wxAppConsole::OnCmdLineHelp(wxCmdLineParser&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x74): undefined reference to `wxAppConsole::OnCmdLineError(wxCmdLineParser&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x78): undefined reference to `wxAppConsole::FilterEvent(wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x7c): undefined reference to `wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x84): undefined reference to `wxAppConsole::ProcessPendingEvents()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x88): undefined reference to `wxApp::Yield(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x8c): undefined reference to `wxApp::WakeUpIdle()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x90): undefined reference to `wxAppBase::CreateTraits()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x94): undefined reference to `wxAppBase::MainLoop()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x98): undefined reference to `wxAppBase::ExitMainLoop()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0x9c): undefined reference to `wxAppBase::Pending()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xa0): undefined reference to `wxAppBase::Dispatch()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xa4): undefined reference to `wxAppBase::ProcessIdle()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xa8): undefined reference to `wxAppBase::SendIdleEvents(wxWindow*, wxIdleEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xac): undefined reference to `wxAppBase::OnExceptionInMainLoop()'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xb4): undefined reference to `wxAppBase::GetTopWindow() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xb8): undefined reference to `wxAppBase::GetDisplayMode() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xc4): undefined reference to `wxAppBase::GetLayoutDirection() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV7MainApp[vtable for MainApp]+0xc8): undefined reference to `wxAppBase::SetActive(bool, wxWindow*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x8): undefined reference to `wxFrame::GetClassInfo() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x14): undefined reference to `wxObject::CreateRefData() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x18): undefined reference to `wxObject::CloneRefData(wxObjectRefData const*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1c): undefined reference to `wxEvtHandler::ProcessEvent(wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x20): undefined reference to `wxEvtHandler::SearchEventTable(wxEventTable&, wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x24): undefined reference to `wxWindowBase::TryValidator(wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x28): undefined reference to `wxWindowBase::TryParent(wxEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x34): undefined reference to `wxEvtHandler::DoSetClientObject(wxClientData*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x38): undefined reference to `wxEvtHandler::DoGetClientObject() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x3c): undefined reference to `wxEvtHandler::DoSetClientData(void*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x40): undefined reference to `wxEvtHandler::DoGetClientData() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x44): undefined reference to `wxTopLevelWindowBase::Destroy()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x58): undefined reference to `wxWindow::GetLayoutDirection() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x5c): undefined reference to `wxWindow::SetLayoutDirection(wxLayoutDirection)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x60): undefined reference to `wxWindow::AdjustForLayoutDirection(int, int, int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x64): undefined reference to `wxTopLevelWindowGTK::Raise()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x68): undefined reference to `wxWindow::Lower()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x70): undefined reference to `wxWindowBase::Fit()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x74): undefined reference to `wxWindowBase::FitInside()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x7c): undefined reference to `wxTopLevelWindowGTK::DoSetSizeHints(int, int, int, int, int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x80): undefined reference to `wxWindowBase::SetVirtualSizeHints(int, int, int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x84): undefined reference to `wxTopLevelWindowBase::SetMinSize(wxSize const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x88): undefined reference to `wxTopLevelWindowBase::SetMaxSize(wxSize const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x94): undefined reference to `wxWindowBase::DoSetVirtualSize(int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x98): undefined reference to `wxWindowBase::DoGetVirtualSize() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xa0): undefined reference to `wxWindowBase::GetWindowBorderSize() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xa4): undefined reference to `wxTopLevelWindowGTK::Show(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xa8): undefined reference to `wxWindow::Enable(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xb4): undefined reference to `wxWindowBase::IsShownOnScreen() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xb8): undefined reference to `wxTopLevelWindowGTK::SetWindowStyleFlag(long)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xc0): undefined reference to `wxWindow::IsRetained() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xc8): undefined reference to `wxWindowBase::MakeModal(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xd4): undefined reference to `wxWindow::SetFocus()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xdc): undefined reference to `wxWindow::AcceptsFocus() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xe4): undefined reference to `wxWindowBase::Navigate(int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xec): undefined reference to `wxWindow::Reparent(wxWindowBase*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xf0): undefined reference to `wxWindow::AddChild(wxWindowBase*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xf4): undefined reference to `wxTopLevelWindowBase::RemoveChild(wxWindowBase*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0xf8): undefined reference to `wxWindowBase::SetValidator(wxValidator const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x100): undefined reference to `wxWindowBase::Validate()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x104): undefined reference to `wxWindowBase::TransferDataToWindow()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x108): undefined reference to `wxWindowBase::TransferDataFromWindow()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x10c): undefined reference to `wxWindowBase::InitDialog()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x114): undefined reference to `wxWindow::WarpPointer(int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x11c): undefined reference to `wxWindow::Refresh(bool, wxRect const*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x120): undefined reference to `wxWindow::Update()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x124): undefined reference to `wxWindow::ClearBackground()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x138): undefined reference to `wxWindow::IsDoubleBuffered() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x13c): undefined reference to `wxWindow::DoIsExposed(int, int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x140): undefined reference to `wxWindow::DoIsExposed(int, int, int, int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x148): undefined reference to `wxWindow::SetBackgroundColour(wxColour const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x14c): undefined reference to `wxWindow::SetForegroundColour(wxColour const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x150): undefined reference to `wxWindow::SetBackgroundStyle(wxBackgroundStyle)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x15c): undefined reference to `wxWindow::SetFont(wxFont const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x160): undefined reference to `wxWindow::SetCursor(wxCursor const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x164): undefined reference to `wxWindow::GetCharHeight() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x168): undefined reference to `wxWindow::GetCharWidth() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x16c): undefined reference to `wxWindow::GetTextExtent(wxString const&, int*, int*, int*, int*, wxFont const*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x170): undefined reference to `wxFrameBase::UpdateWindowUI(long)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x174): undefined reference to `wxTopLevelWindowBase::DoUpdateWindowUI(wxUpdateUIEvent&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x17c): undefined reference to `wxWindow::SetScrollbar(int, int, int, int, bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x180): undefined reference to `wxWindow::SetScrollPos(int, int, bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x184): undefined reference to `wxWindow::GetScrollPos(int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x188): undefined reference to `wxWindow::GetScrollThumb(int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x18c): undefined reference to `wxWindow::GetScrollRange(int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x190): undefined reference to `wxWindow::ScrollWindow(int, int, wxRect const*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x194): undefined reference to `wxWindow::ScrollLines(int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x198): undefined reference to `wxWindow::ScrollPages(int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x19c): undefined reference to `wxWindowBase::GetHelpTextAtPoint(wxPoint const&, wxHelpEvent::Origin) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1a0): undefined reference to `wxWindow::SetDropTarget(wxDropTarget*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1a8): undefined reference to `wxWindowBase::SetConstraintSizes(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1ac): undefined reference to `wxWindowBase::LayoutPhase1(int*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1b0): undefined reference to `wxWindowBase::LayoutPhase2(int*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1b4): undefined reference to `wxWindowBase::DoPhase(int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1b8): undefined reference to `wxWindowBase::SetSizeConstraint(int, int, int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1bc): undefined reference to `wxWindowBase::MoveConstraint(int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1c0): undefined reference to `wxWindowBase::GetSizeConstraint(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1c4): undefined reference to `wxWindowBase::GetClientSizeConstraint(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1c8): undefined reference to `wxWindowBase::GetPositionConstraint(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1cc): undefined reference to `wxWindowBase::Layout()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1d0): undefined reference to `wxTopLevelWindowGTK::SetTransparent(unsigned char)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1d4): undefined reference to `wxTopLevelWindowGTK::CanSetTransparent()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1d8): undefined reference to `wxFrame::OnInternalIdle()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1e8): undefined reference to `wxWindowBase::InheritAttributes()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1f0): undefined reference to `wxWindow::DoMoveInTabOrder(wxWindow*, wxWindowBase::MoveKind)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x1f8): undefined reference to `wxWindowBase::GetDefaultBorder() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x200): undefined reference to `wxTopLevelWindowBase::DoClientToScreen(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x204): undefined reference to `wxTopLevelWindowBase::DoScreenToClient(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x208): undefined reference to `wxWindowBase::DoHitTest(int, int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x20c): undefined reference to `wxWindow::DoCaptureMouse()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x210): undefined reference to `wxWindow::DoReleaseMouse()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x214): undefined reference to `wxWindow::DoGetPosition(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x21c): undefined reference to `wxWindow::DoGetSize(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x220): undefined reference to `wxFrame::DoGetClientSize(int*, int*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x224): undefined reference to `wxWindowBase::DoGetBestSize() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x22c): undefined reference to `wxTopLevelWindowGTK::DoSetSize(int, int, int, int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x230): undefined reference to `wxFrame::DoSetClientSize(int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x234): undefined reference to `wxTopLevelWindowGTK::DoMoveWindow(int, int, int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x238): undefined reference to `wxTopLevelWindowBase::DoCentre(int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x23c): undefined reference to `wxWindow::DoSetToolTip(wxToolTip*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x240): undefined reference to `wxWindow::DoPopupMenu(wxMenu*, int, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x244): undefined reference to `wxWindowBase::AdjustForParentClientOrigin(int&, int&, int) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x248): undefined reference to `wxWindowBase::DoSetWindowVariant(wxWindowVariant)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x250): undefined reference to `wxWindow::GetConnectWidget()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x254): undefined reference to `wxWindow::GTKProcessEvent(wxEvent&) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x258): undefined reference to `wxWindow::GTKWidgetNeedsMnemonic() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x25c): undefined reference to `wxWindow::GTKWidgetDoSetMnemonic(_GtkWidget*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x260): undefined reference to `wxWindow::GTKGetWindow(wxArrayGdkWindows&) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x264): undefined reference to `wxWindow::ApplyToolTip(_GtkTooltips*, wchar_t const*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x274): undefined reference to `wxWindow::ApplyWidgetStyle(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x278): undefined reference to `wxWindow::DoApplyWidgetStyle(_GtkRcStyle*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x27c): undefined reference to `wxTopLevelWindowGTK::Maximize(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x280): undefined reference to `wxTopLevelWindowGTK::Restore()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x284): undefined reference to `wxTopLevelWindowGTK::Iconize(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x288): undefined reference to `wxTopLevelWindowGTK::IsMaximized() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x28c): undefined reference to `wxTopLevelWindowBase::IsAlwaysMaximized() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x290): undefined reference to `wxTopLevelWindowGTK::IsIconized() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x294): undefined reference to `wxTopLevelWindowGTK::SetIcon(wxIcon const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x298): undefined reference to `wxTopLevelWindowGTK::SetIcons(wxIconBundle const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x29c): undefined reference to `wxTopLevelWindowGTK::ShowFullScreen(bool, long)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2a4): undefined reference to `wxTopLevelWindowGTK::SetTitle(wxString const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2ac): undefined reference to `wxTopLevelWindowGTK::EnableCloseButton(bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2b0): undefined reference to `wxTopLevelWindowGTK::SetShape(wxRegion const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2b4): undefined reference to `wxTopLevelWindowGTK::RequestUserAttention(int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2b8): undefined reference to `wxTopLevelWindowGTK::IsActive()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2c4): undefined reference to `wxTopLevelWindowBase::GetRectForTopLevelChildren(int*, int*, int*, int*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2c8): undefined reference to `wxFrameBase::IsOneOfBars(wxWindow const*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2cc): undefined reference to `wxTopLevelWindowGTK::AddGrab()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2d0): undefined reference to `wxTopLevelWindowGTK::RemoveGrab()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2d8): undefined reference to `wxFrame::GtkOnSize()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2dc): undefined reference to `wxFrameBase::SendSizeEvent()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2e0): undefined reference to `wxFrameBase::SetMenuBar(wxMenuBar*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2e8): undefined reference to `wxFrame::CreateStatusBar(int, long, int, wxString const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2ec): undefined reference to `wxFrameBase::OnCreateStatusBar(int, long, int, wxString const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2f4): undefined reference to `wxFrame::SetStatusBar(wxStatusBar*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2f8): undefined reference to `wxFrameBase::SetStatusText(wxString const&, int)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x2fc): undefined reference to `wxFrameBase::SetStatusWidths(int, int const*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x300): undefined reference to `wxFrame::CreateToolBar(long, int, wxString const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x304): undefined reference to `wxFrameBase::OnCreateToolBar(long, int, wxString const&)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x30c): undefined reference to `wxFrame::SetToolBar(wxToolBar*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x310): undefined reference to `wxFrameBase::DoMenuUpdates(wxMenu*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x314): undefined reference to `wxFrameBase::DoGiveHelp(wxString const&, bool)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x31c): undefined reference to `wxFrame::DetachMenuBar()'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x320): undefined reference to `wxFrame::AttachMenuBar(wxMenuBar*)'
/tmp/ccV3wCsk.o:(.rodata._ZTV9MainFrame[vtable for MainFrame]+0x324): undefined reference to `wxFrame::PositionStatusBar()'
/tmp/ccV3wCsk.o:(.rodata._ZTV20wxThreadHelperThread[vtable for wxThreadHelperThread]+0xc): undefined reference to `wxThread::TestDestroy()'
/tmp/ccV3wCsk.o:(.rodata._ZTI9MainFrame[typeinfo for MainFrame]+0x8): undefined reference to `typeinfo for wxFrame'
/tmp/ccV3wCsk.o:(.rodata._ZTI7MainApp[typeinfo for MainApp]+0x8): undefined reference to `typeinfo for wxApp'
/tmp/ccV3wCsk.o:(.rodata._ZTI20wxThreadHelperThread[typeinfo for wxThreadHelperThread]+0x8): undefined reference to `typeinfo for wxThread'
/tmp/ccV3wCsk.o:(.rodata._ZTV14wxMenuItemList[vtable for wxMenuItemList]+0x8): undefined reference to `wxObject::GetClassInfo() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV14wxMenuItemList[vtable for wxMenuItemList]+0x14): undefined reference to `wxObject::CreateRefData() const'
/tmp/ccV3wCsk.o:(.rodata._ZTV14wxMenuItemList[vtable for wxMenuItemList]+0x18): undefined reference to `wxObject::CloneRefData(wxObjectRefData const*) const'
/tmp/ccV3wCsk.o:(.rodata._ZTI14wxMenuItemList[typeinfo for wxMenuItemList]+0x8): undefined reference to `typeinfo for wxListBase'
collect2: ld returned 1 exit status

```

---

### Post by SledgeHammer_999 on 2008-10-04
As I said above you need 2 builds of wxWidgets. One dynamic and one static. Ubuntu provides dynamic. The way I solved it was to build the sources on my own and install them in a folder in my home folder. This custom build creates another "wx-config" script which works with the --static switch.

---

### Post by WitchCraft on 2008-10-04
> **SledgeHammer_999 said:**
> As I said above you need 2 builds of wxWidgets. One dynamic and one static. Ubuntu provides dynamic. The way I solved it was to build the sources on my own and install them in a folder in my home folder. This custom build creates another "wx-config" script which works with the --static switch.

OK, looks like there is no other way, so I'm gonna do the same.

Thanks anyway !

---

### Post by bossfn on 2008-12-08
> **SledgeHammer_999 said:**
> As I said above you need 2 builds of wxWidgets. One dynamic and one static. Ubuntu provides dynamic. The way I solved it was to build the sources on my own and install them in a folder in my home folder. This custom build creates another "wx-config" script which works with the --static switch.


Any chance you can provide instructions on how to do that step (build sources and install them so it works with static)?

---

### Post by WitchCraft on 2008-12-08
> **bossfn said:**
> Any chance you can provide instructions on how to do that step (build sources and install them so it works with static)?

extract the source somewhere.
create a wxwin environment variable to point to the directory where you extracted wxwidgets
add $wxwin$ to the path environment variable.

Get the gtk+ 2.0 development files.
sudo apt-get install libgtk2.0-dev libgnome2-dev

```

./configure --enable-optimise --enable-stl --enable-unicode 
  --enable-threads --enable-static --disable-shared --enable-monolithic --enable-graphics_ctx

```(takes appx 5 minutes)

make
(takes appx. 20 min to one hour)

make install

Now update the default to the latest build.
update-alternatives --config wx-config



```

./configure --help
`configure' configures wxWidgets 2.8.9 to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
              [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
              [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --datadir=DIR          read-only architecture-independent data [PREFIX/share]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --infodir=DIR          info documentation [PREFIX/info]
  --mandir=DIR           man documentation [PREFIX/man]

X features:
  --x-includes=DIR    X include files are in DIR
  --x-libraries=DIR   X library files are in DIR

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]
  --target=TARGET   configure for building compilers for TARGET [HOST]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --enable-gui            use GUI classes
  --enable-monolithic     build wxWidgets as single library
  --enable-plugins        build parts of wxWidgets as loadable components
  --enable-universal      use wxWidgets GUI controls instead of native ones
  --enable-nanox          use NanoX
  --disable-gtk2          use GTK+ 1.2 instead of 2.0
  --enable-gpe            use GNOME PDA Environment features if possible
  --enable-shared         create shared library code
  --enable-optimise       compile without optimisations
  --enable-debug          same as debug_flag and debug_info
  --enable-stl            use STL for containers
  --enable-omf            use OMF object format
  --enable-debug_flag     set __WXDEBUG__ flag (recommended for developers!)
  --enable-debug_info     create code with debugging information
  --enable-debug_gdb      create code with extra GDB debugging information
  --enable-debug_cntxt    use wxDebugContext
  --enable-mem_tracing    create code with memory tracing
  --enable-profile        create code with profiling information
  --enable-no_rtti        create code without RTTI information
  --enable-no_exceptions  create code without C++ exceptions handling
  --enable-permissive     compile code disregarding strict ANSI
  --enable-no_deps        create code without dependency information
  --disable-vararg_macros don't use vararg macros, even if they are supported
  --enable-universal_binary  create Mac PowerPC and Intel Universal binary
  --enable-compat24       enable wxWidgets 2.4 compatibility
  --disable-compat26      disable wxWidgets 2.6 compatibility
  --disable-rpath         disable use of rpath for uninstalled builds
  --enable-objc_uniquifying enable Objective-C class name uniquifying
  --enable-abi-incompatible-features Enables features that break ABI compatibility
  --enable-intl           use internationalization system
  --enable-config         use wxConfig (and derived) classes
  --enable-protocols      use wxProtocol and derived classes
  --enable-ftp            use wxFTP (requires wxProtocol
  --enable-http           use wxHTTP (requires wxProtocol
  --enable-fileproto      use wxFileProto class (requires wxProtocol
  --enable-sockets        use socket/network classes
  --enable-ole            use OLE classes (Win32 only)
  --enable-dataobj        use data object classes
  --enable-ipc            use interprocess communication (wxSocket etc.)
  --enable-apple_ieee     use the Apple IEEE codec
  --enable-arcstream      use wxArchive streams
  --enable-backtrace      use wxStackWalker class for getting backtraces
  --enable-catch_segvs    catch signals in wxApp::OnFatalException (Unix only)
  --enable-cmdline        use wxCmdLineParser class
  --enable-datetime       use wxDateTime class
  --enable-debugreport    use wxDebugReport class
  --enable-dialupman      use dialup network classes
  --enable-dynlib         use wxLibrary class for DLL loading
  --enable-dynamicloader  use (new) wxDynamicLibrary class
  --enable-exceptions     build exception-safe library
  --enable-ffile          use wxFFile class
  --enable-file           use wxFile class
  --enable-filesystem     use virtual file systems classes
  --enable-fontmap        use font encodings conversion classes
  --enable-fs_archive     use virtual archive filesystems
  --enable-fs_inet        use virtual HTTP/FTP filesystems
  --enable-fs_zip         now replaced by fs_archive
  --enable-geometry       use geometry class
  --enable-log            use logging system
  --enable-longlong       use wxLongLong class
  --enable-mimetype       use wxMimeTypesManager
  --enable-mslu           use MS Layer for Unicode on Windows 9x (Win32 only)
  --enable-snglinst       use wxSingleInstanceChecker class
  --enable-std_iostreams  use standard C++ stream classes
  --enable-std_string     use standard C++ string classes
  --enable-stdpaths       use wxStandardPaths class
  --enable-stopwatch      use wxStopWatch class
  --enable-streams        use wxStream etc classes
  --enable-sysoptions     use wxSystemOptions
  --enable-tarstream      use wxTar streams
  --enable-textbuf        use wxTextBuffer class
  --enable-textfile       use wxTextFile class
  --enable-timer          use wxTimer class
  --enable-unicode        compile wxString with Unicode support
  --enable-sound          use wxSound class
  --enable-mediactrl      use wxMediaCtrl class
  --enable-gstreamer8     force GStreamer 0.8 instead of 0.10 with the wxMediaCtrl class on unix
  --enable-printfposparam use wxVsnprintf() which supports positional parameters
  --enable-zipstream      use wxZip streams
  --enable-url            use wxURL class
  --enable-variant        use wxVariant class
  --enable-protocol       use wxProtocol class
  --enable-protocol-http  HTTP support in wxProtocol
  --enable-protocol-ftp   FTP support in wxProtocol
  --enable-protocol-file  FILE support in wxProtocol
  --enable-threads        use threads
  --enable-docview        use document view architecture
  --enable-help           use help subsystem
  --enable-mshtmlhelp     use MS HTML Help (win32)
  --enable-html           use wxHTML sub-library
  --enable-htmlhelp       use wxHTML-based help
  --enable-xrc            use XRC resources sub-library
  --enable-aui            use AUI docking library
  --enable-constraints    use layout-constraints system
  --enable-printarch      use printing architecture
  --enable-mdi            use multiple document interface architecture
  --enable-mdidoc         use docview architecture with MDI
  --enable-loggui         use standard GUI logger
  --enable-logwin         use wxLogWindow
  --enable-logdialog      use wxLogDialog
  --enable-webkit         use wxWebKitCtrl (Mac)
  --enable-richtext       use wxRichTextCtrl
  --enable-graphics_ctx   use graphics context 2D drawing API
  --enable-postscript     use wxPostscriptDC device context (default for gtk+)
  --enable-prologio       not available; see contrib
  --enable-resources      not available; see contrib
  --enable-clipboard      use wxClipboard class
  --enable-dnd            use Drag'n'Drop classes
  --enable-metafile       use win32 metafiles
  --enable-controls       use all usual controls
  --enable-accel          use accelerators
  --enable-animatectrl    use wxAnimationCtrl class
  --enable-button         use wxButton class
  --enable-bmpbutton      use wxBitmapButton class
  --enable-bmpcombobox    use wxBitmapComboBox class
  --enable-calendar       use wxCalendarCtrl class
  --enable-caret          use wxCaret class
  --enable-checkbox       use wxCheckBox class
  --enable-checklst       use wxCheckListBox (listbox with checkboxes) class
  --enable-choice         use wxChoice class
  --enable-choicebook     use wxChoicebook class
  --enable-collpane       use wxCollapsiblePane class
  --enable-colourpicker   use wxColourPickerCtrl class
  --enable-combobox       use wxComboBox class
  --enable-comboctrl      use wxComboCtrl class
  --enable-datepick       use wxDatePickerCtrl class
  --enable-dirpicker      use wxDirPickerCtrl class
  --enable-display        use wxDisplay class
  --enable-detect_sm      use code to detect X11 session manager
  --enable-filepicker     use wxFilePickerCtrl class
  --enable-fontpicker     use wxFontPickerCtrl class
  --enable-gauge          use wxGauge class
  --enable-grid           use wxGrid class
  --enable-dataviewctrl   use wxDataViewCtrl class
  --enable-hyperlink      use wxHyperlinkCtrl class
  --enable-imaglist       use wxImageList class
  --enable-listbook       use wxListbook class
  --enable-listbox        use wxListBox class
  --enable-listctrl       use wxListCtrl class
  --enable-notebook       use wxNotebook class
  --enable-odcombobox     use wxOwnerDrawnComboBox class
  --enable-radiobox       use wxRadioBox class
  --enable-radiobtn       use wxRadioButton class
  --enable-sash           use wxSashWindow class
  --enable-scrollbar      use wxScrollBar class and scrollable windows
  --enable-searchctrl     use wxSearchCtrl class
  --enable-slider         use wxSlider class
  --enable-spinbtn        use wxSpinButton class
  --enable-spinctrl       use wxSpinCtrl class
  --enable-splitter       use wxSplitterWindow class
  --enable-statbmp        use wxStaticBitmap class
  --enable-statbox        use wxStaticBox class
  --enable-statline       use wxStaticLine class
  --enable-stattext       use wxStaticText class
  --enable-statusbar      use wxStatusBar class
  --enable-tabdialog      use wxTabControl class
  --enable-textctrl       use wxTextCtrl class
  --enable-togglebtn      use wxToggleButton class
  --enable-toolbar        use wxToolBar class
  --enable-tbarnative     use native wxToolBar class
  --enable-treebook       use wxTreebook class
  --enable-toolbook       use wxToolbook class
  --enable-treectrl       use wxTreeCtrl class
  --enable-tipwindow      use wxTipWindow class
  --enable-popupwin       use wxPopUpWindow class
  --enable-commondlg      use all common dialogs
  --enable-aboutdlg       use wxAboutBox
  --enable-choicedlg      use wxChoiceDialog
  --enable-coldlg         use wxColourDialog
  --enable-filedlg        use wxFileDialog
  --enable-finddlg        use wxFindReplaceDialog
  --enable-fontdlg        use wxFontDialog
  --enable-dirdlg         use wxDirDialog
  --enable-msgdlg         use wxMessageDialog
  --enable-numberdlg      use wxNumberEntryDialog
  --enable-splash         use wxSplashScreen
  --enable-textdlg        use wxTextDialog
  --enable-tipdlg         use startup tips
  --enable-progressdlg    use wxProgressDialog
  --enable-wizarddlg      use wxWizard
  --enable-menus          use wxMenu/wxMenuBar/wxMenuItem classes
  --enable-miniframe      use wxMiniFrame class
  --enable-tooltips       use wxToolTip class
  --enable-splines        use spline drawing code
  --enable-mousewheel     use mousewheel
  --enable-validators     use wxValidator and derived classes
  --enable-busyinfo       use wxBusyInfo
  --enable-joystick       use wxJoystick
  --enable-metafiles      use wxMetaFile (Win32 only)
  --enable-dragimage      use wxDragImage
  --enable-accessibility  enable accessibility support
  --enable-dccache        cache temporary wxDC objects (Win32 only)
  --enable-palette        use wxPalette class
  --enable-image          use wxImage class
  --enable-gif            use gif images (GIF file format)
  --enable-pcx            use pcx images (PCX file format)
  --enable-tga            use tga images (TGA file format)
  --enable-iff            use iff images (IFF file format)
  --enable-pnm            use pnm images (PNM file format)
  --enable-xpm            use xpm images (XPM file format)
  --enable-icocur         use Windows ICO and CUR formats
  --enable-official_build official build of wxWidgets (win32 DLL only)
  --enable-vendor=VENDOR  vendor name (win32 DLL only)
  --disable-largefile     omit support for large files
  --disable-gtktest       do not try to compile and run a test GTK+ program
  --disable-gtktest       Do not try to compile and run a test GTK program
  --disable-sdltest       Do not try to compile and run a test SDL program
  --enable-omf            use OMF object format (OS/2)
  --disable-dependency-tracking
                          don't use dependency tracking even if the compiler
                          can
  --disable-precomp-headers
                          don't use precompiled headers even if compiler can

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --without-subdirs       don't generate makefiles for samples/demos/...
  --with-gtk[=VERSION]    use GTK+, VERSION can be 2 (default), 1 or "any"
  --with-motif            use Motif/Lesstif
  --with-mac              use Mac OS X
  --with-cocoa            use Cocoa
  --with-wine             use Wine
  --with-msw              use MS-Windows
  --with-pm               use OS/2 Presentation Manager
  --with-mgl              use SciTech MGL
  --with-directfb         use DirectFB
  --with-microwin         use MicroWindows
  --with-x11              use X11
  --with-libpng           use libpng (PNG image format)
  --with-libjpeg          use libjpeg (JPEG file format)
  --with-libtiff          use libtiff (TIFF file format)
  --with-libxpm           use libxpm (XPM file format)
  --with-libmspack        use libmspack (CHM help files loading)
  --with-sdl              use SDL for audio on Unix
  --with-gnomeprint       use GNOME print for printing under GNOME
  --with-gnomevfs         use GNOME VFS for associating MIME types
  --with-hildon           use Hildon framework for Nokia 770
  --with-opengl           use OpenGL (or Mesa)
  --with-themes=all|list  use only the specified comma-separated list of wxUniversal themes
  --with-dmalloc          use dmalloc library (http://dmalloc.com/)
  --with-regex            enable support for wxRegEx class
  --with-zlib             use zlib for LZW compression
  --with-odbc             use the IODBC and wxODBC classes
  --with-expat            enable XML support using expat parser
  --with-macosx-sdk=PATH  use an OS X SDK at PATH
  --with-macosx-version-min=VER   build binaries which require at least this OS X version
  --with-flavour=NAME     specify a name to identify this build
  --with-gtk-prefix=PFX   Prefix where GTK is installed (optional)
  --with-gtk-exec-prefix=PFX Exec prefix where GTK is installed (optional)
  --with-x                use the X Window System
  --with-libiconv-prefix=DIR  search for libiconv in DIR/include and DIR/lib
  --with-sdl-prefix=PFX   Prefix where SDL is installed (optional)
  --with-sdl-exec-prefix=PFX Exec prefix where SDL is installed (optional)
  --with-cppunit-prefix=PFX   Prefix where CppUnit is installed (optional)
  --with-cppunit-exec-prefix=PFX  Exec prefix where CppUnit is installed (optional)

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++ preprocessor flags, e.g. -I<include dir> if you have
              headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  PKG_CONFIG  path to pkg-config utility
  DIRECTFB_CFLAGS
              C compiler flags for DIRECTFB, overriding pkg-config
  DIRECTFB_LIBS
              linker flags for DIRECTFB, overriding pkg-config
  PANGOX_CFLAGS
              C compiler flags for PANGOX, overriding pkg-config
  PANGOX_LIBS linker flags for PANGOX, overriding pkg-config
  PANGOFT2_CFLAGS
              C compiler flags for PANGOFT2, overriding pkg-config
  PANGOFT2_LIBS
              linker flags for PANGOFT2, overriding pkg-config
  PANGOXFT_CFLAGS
              C compiler flags for PANGOXFT, overriding pkg-config
  PANGOXFT_LIBS
              linker flags for PANGOXFT, overriding pkg-config
  LIBGNOMEPRINTUI_CFLAGS
              C compiler flags for LIBGNOMEPRINTUI, overriding pkg-config
  LIBGNOMEPRINTUI_LIBS
              linker flags for LIBGNOMEPRINTUI, overriding pkg-config
  GNOMEVFS_CFLAGS
              C compiler flags for GNOMEVFS, overriding pkg-config
  GNOMEVFS_LIBS
              linker flags for GNOMEVFS, overriding pkg-config
  HILDON_CFLAGS
              C compiler flags for HILDON, overriding pkg-config
  HILDON_LIBS linker flags for HILDON, overriding pkg-config
  CAIRO_CFLAGS
              C compiler flags for CAIRO, overriding pkg-config
  CAIRO_LIBS  linker flags for CAIRO, overriding pkg-config
  GST_CFLAGS  C compiler flags for GST, overriding pkg-config
  GST_LIBS    linker flags for GST, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

```sudo updatedb
locate wx_ | sed '/doc/d;/\/usr\/l/d'


```

A$$HAT@toshiba:/usr/src/wxWidgets-2.8.9# ./wx-config --version=2.8 --static --libs
-L/usr/src/wxWidgets-2.8.9/lib -pthread   /usr/src/wxWidgets-2.8.9/lib/libwx_gtk2u-2.8.a -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lgio-2.0 -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0 -lXinerama -lSM -lpng -lz -ljpeg -ltiff -lwxregexu-2.8 -lz -ldl -lm 

```Compile programs (with repository wxwidgets [dynamically linked]):
```

g++ -Wall -o UrThack injector.cpp `wx-config --version=2.8 --static=no --libs` `wx-config --version=2.8 --static=no --cxxflags` 

```--> Filesize: 262.9 KB (269232 bytes)


Compile programs (with compiled wxwidgets [statically linked]):
```

g++ -Wall -o UrThack injector.cpp `wx-config --version=2.8 --static=yes --libs` `wx-config --version=2.8 --static=yes --cxxflags`

```--> Filesize: 3.5 MB (3646347 bytes)


YES !

---

### Post by lollobrigido on 2010-02-10
For me this thread is not SOLVED, because if I follow these instructions I'm not be able to use wxwidget to obtain a statically linked application.
I'm using ubuntu 9.10, g++ (Ubuntu 4.4.1-4ubuntu9) 4.4.1 and , wxWidgets 2.8.10 compiled statically (and dynamic) with:
```
./configure --disable-shared --enable-static
```
(with the flags i the previous reply i obtain the same trouble)
I compiled wxWidget dinamically too, and the application is compiled well, so I think the wx-config is the right one.
When I compile my app statically I use this command to get the libs for the linker:
for the compiler
```
wx-config --static=yes --cxxflags
```
for the linker
```
wx-config --static=yes --libs
```
In the link pass I obtain tons of "undefined..." 
If I compile with
```
wx-config --static=no --cxxflags
``` and
```
wx-config --static=no --libs
```
everithing go well.

Please someone can help me? 
Lollo

---

