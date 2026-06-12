---
title: "Help compiling Falling Sands"
date: 2007-08-04
forum: Packaging and Compiling Programs
---

### Post by Frak on 2007-08-04
I am trying to create a .deb for fsg-4.4 (Falling Sand Game), and whenever I try to compile it, I keep receiving errors for wxWidgets.
```
frak@frak-desktop:~/Desktop/fsg$ make
g++ -c -Wall -pipe -O3 -funroll-loops -Wall -DVERSION="\"4.4\"" -DCVERSION="\"`date +%Y%m%d`\"" -ggdb MainFrame.cpp `wx-config --cxxflags` -o MainFrame.o 
/usr/include/wx-2.8/wx/hashmap.h: In member function ‘wxLongToLongHashMap_wxImplementation_HashTable::Node** wxLongToLongHashMap_wxImplementation_HashTable::GetNodePtr(const long int&) const’:
/usr/include/wx-2.8/wx/hashmap.h:714: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.8/wx/clntdata.h: In member function ‘wxShadowObjectMethods_wxImplementation_HashTable::Node** wxShadowObjectMethods_wxImplementation_HashTable::GetNodePtr(const wxString&) const’:
/usr/include/wx-2.8/wx/clntdata.h:20: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.8/wx/clntdata.h: In member function ‘wxShadowObjectFields_wxImplementation_HashTable::Node** wxShadowObjectFields_wxImplementation_HashTable::GetNodePtr(const wxString&) const’:
/usr/include/wx-2.8/wx/clntdata.h:25: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.8/wx/gdicmn.h: In member function ‘wxStringToColourHashMap_wxImplementation_HashTable::Node** wxStringToColourHashMap_wxImplementation_HashTable::GetNodePtr(const wxString&) const’:
/usr/include/wx-2.8/wx/gdicmn.h:544: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/include/wx-2.8/wx/image.h: In member function ‘wxImageHistogramBase_wxImplementation_HashTable::Node** wxImageHistogramBase_wxImplementation_HashTable::GetNodePtr(const long unsigned int&) const’:
/usr/include/wx-2.8/wx/image.h:136: warning: dereferencing type-punned pointer will break strict-aliasing rules
MainFrame.cpp: In function ‘void loadFileError(int, wxString)’:
MainFrame.cpp:312: error: no matching function for call to ‘wxString::Printf(const char [21], int&, const wxChar*)’
/usr/include/wx-2.8/wx/string.h:1149: note: candidates are: int wxString::Printf(const wxChar*, ...)
MainFrame.cpp: In member function ‘void MainFrame::loadPhysics(wxString)’:
MainFrame.cpp:387: error: cannot convert ‘wxString’ to ‘const char*’ for argument ‘1’ to ‘FILE* fopen(const char*, const char*)’
MainFrame.cpp:430: error: call of overloaded ‘wxString(char [128])’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:470: error: call of overloaded ‘wxString(char [128])’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:496: error: call of overloaded ‘wxString(char [128])’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:498: error: call of overloaded ‘wxString(char [128])’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:500: error: call of overloaded ‘wxString(char [128])’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:526: error: call of overloaded ‘wxString(char [200])’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:536: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:542: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:607: error: call of overloaded ‘wxString(char [128])’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:645: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:673: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:690: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:723: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:758: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:798: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:831: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:833: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:864: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:866: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:912: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:914: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:944: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:946: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:948: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:984: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:986: error: call of overloaded ‘wxString(char*&)’ is ambiguous
/usr/include/wx-2.8/wx/string.h:722: note: candidates are: wxString::wxString(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:692: note:                 wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:690: note:                 wxString::wxString(const wxString&) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
MainFrame.cpp:1011: error: no matching function for call to ‘wxString::Printf(const char [64], int&)’
/usr/include/wx-2.8/wx/string.h:1149: note: candidates are: int wxString::Printf(const wxChar*, ...)
make: *** [MainFrame.o] Error 1
```

Any ideas :confused:
Its a really fun Game/Simulator, and deserves to have the honor of being a Debian package :)

---

### Post by ericpierce on 2008-05-04
I don't know much about wxWidgets, but it looks like he hasn't updated his code for the newer versions of wxWidgets that have built in unicode support.

Below is a patch that updates fsg-4.4 to the latest wxWidgets 2.8.*.

So grab the 4.4 source from [http://www.piettes.com/fallingsandgame/fsg-4.4](http://www.piettes.com/fallingsandgame/fsg-4.4)

To apply the patch, copy/paste the diff code below into a file called 'fsg_4.4-wx2.8.patch'.  Place this file into the /fsg-4.4 directory.  Go into that directory and type:  patch -p0 -u < fsg_4.4-wx2.8.patch

Then you can type 'make' to compile, and you should end up with a binary.  Type './sand' to run it.  

You're on your own for creating a deb package (I always use 'checkinstall' myself).

Eric Pierce

```

diff -ruNp ./Canvas.cpp ../fsg-4.4_unicode/Canvas.cpp
--- ./Canvas.cpp	2006-12-29 16:26:56.000000000 -0600
+++ ../fsg-4.4_unicode/Canvas.cpp	2008-05-04 12:05:04.000000000 -0500
@@ -882,7 +882,7 @@ void Canvas::calculate(){
 void Canvas::Refresh(){
 
   wxString str(_(""));
-  str.Printf(_("%s [%d]"), names[data[(g_width*mousey)+mousex]].c_str(), int(energy[(g_width*mousey)+mousex]));
+  str.Printf(wxT("%s [%d]"), names[data[(g_width*mousey)+mousex]].c_str(), int(energy[(g_width*mousey)+mousex]));
   statusbar->SetStatusText(str, 2);
 
 
@@ -924,13 +924,12 @@ void Canvas::OnTimer(wxTimerEvent& event
 
 void Canvas::OnSecondTimer(wxTimerEvent& event){
   wxString str(_(""));
-  str.Printf(_("%d fps"), frameCount);
+  str.Printf(wxT("%d fps"), frameCount);
   frameCount = 0;
   statusbar->SetStatusText(str,0);
 
   wxString str2(_(""));
-  str2.Printf(_("%02d:%02d"), wxDateTime::Now().Subtract(startTime).GetHours(), 
-	     wxDateTime::Now().Subtract(startTime).GetMinutes());
+  str2.Printf(wxT("%02d:%02d"), wxDateTime::Now().Subtract(startTime).GetHours(), wxDateTime::Now().Subtract(startTime).GetMinutes());
   statusbar->SetStatusText(str2,1);
 }
 
@@ -1006,8 +1005,8 @@ void Canvas::OnMouseMove(wxMouseEvent& e
     
     mouseIsDown = false;
 
-    wxString str("");
-    str.Printf(_("%s [%d]"), names[data[(g_width*mousey)+mousex]].c_str(), (int)energy[(g_width*mousey)+mousex]);
+    wxString str(wxT(""));
+    str.Printf(wxT("%s [%d]"), names[data[(g_width*mousey)+mousex]].c_str(), (int)energy[(g_width*mousey)+mousex]);
     statusbar->SetStatusText(str, 2);
   }
 }
diff -ruNp ./DownloadFileDialog.cpp ../fsg-4.4_unicode/DownloadFileDialog.cpp
--- ./DownloadFileDialog.cpp	2006-12-29 16:26:56.000000000 -0600
+++ ../fsg-4.4_unicode/DownloadFileDialog.cpp	2008-05-04 11:54:58.000000000 -0500
@@ -25,12 +25,12 @@ DownloadFileDialog::DownloadFileDialog(c
   
 
 
-  wxURL listURL("http://www.fallingsandgame.com/wiki/index.php/WxSand_Mods");
+  wxURL listURL(wxT("http://www.fallingsandgame.com/wiki/index.php/WxSand_Mods"));
   //listURL.SetProxy("207.32.43.252:8080");
 
   wxInputStream* is = listURL.GetInputStream();
   if (is == NULL){
-    wxMessageDialog* msg  = new wxMessageDialog(this, "Error connecting to the internet.");
+    wxMessageDialog* msg  = new wxMessageDialog(this, wxT("Error connecting to the internet."));
     msg->ShowModal();
     return;
   }
@@ -39,28 +39,28 @@ DownloadFileDialog::DownloadFileDialog(c
 
   wxString line;
   int index = 0;
-  while(!line.Contains("</body>")){
+  while(!line.Contains(wxT("</body>"))){
     line = tis->ReadLine();
     wxString url = line;
     wxString description1 = line;
     wxString description2 = line;
-    if (line.Contains("<li>")){
-      int startIndex = line.Find("href=\"");
+    if (line.Contains(wxT("<li>"))){
+      int startIndex = line.Find(wxT("href=\""));
       url = line.Mid(startIndex+6);
-      int endIndex = url.Find("\"");
+      int endIndex = url.Find(wxT("\""));
       url = url.Mid(0,endIndex);
       urlArray[index] = url;
       ++index;
 
-      startIndex = description1.Find("<li>");
+      startIndex = description1.Find(wxT("<li>"));
       description1 = description1.Mid(startIndex+4);
-      startIndex = description1.Find(">");
+      startIndex = description1.Find(wxT(">"));
       description1 = description1.Mid(startIndex+1);
 
-      endIndex = description1.Find("</a>");
+      endIndex = description1.Find(wxT("</a>"));
       description1 = description1.Mid(0,endIndex);
 
-      startIndex = description2.Find("</a>");
+      startIndex = description2.Find(wxT("</a>"));
       description2 = description2.Mid(startIndex+4);
 
       lbPhysicsChoices->Append(description1 + description2);
@@ -92,7 +92,7 @@ void DownloadFileDialog::OnOK(wxCommandE
 
   wxTextInputStream* tis = new wxTextInputStream(*(is));
 
-  wxTextFile of("downloadedPhysics.txt");
+  wxTextFile of(wxT("downloadedPhysics.txt"));
   if (of.Exists()){
     of.Open();
     of.Clear();
@@ -105,11 +105,11 @@ void DownloadFileDialog::OnOK(wxCommandE
   int count = 0;
   while(!is->Eof() && state < 2 && count < 10000){
     wxString line = tis->ReadLine();
-    if (line.Contains("<pre>")){
+    if (line.Contains(wxT("<pre>"))){
 	state = 1;
 	continue;
     }
-    if (line.Contains("</pre>"))
+    if (line.Contains(wxT("</pre>")))
 	state = 2;
 
     if (state == 1){
@@ -120,7 +120,7 @@ void DownloadFileDialog::OnOK(wxCommandE
   }
 
   if (state != 2){
-    wxMessageDialog* msg  = new wxMessageDialog(this, "Couldn't find the physics file on the Wiki page.");
+    wxMessageDialog* msg  = new wxMessageDialog(this, wxT("Couldn't find the physics file on the Wiki page."));
     msg->ShowModal();
     of.Write();
     of.Close();
diff -ruNp ./MainFrame.cpp ../fsg-4.4_unicode/MainFrame.cpp
--- ./MainFrame.cpp	2006-12-29 16:26:56.000000000 -0600
+++ ../fsg-4.4_unicode/MainFrame.cpp	2008-05-04 12:17:06.000000000 -0500
@@ -309,7 +309,7 @@ void MainFrame::loadSandbox(wxString fil
 
 void loadFileError(int lineNumber, const wxString message){
   wxString str(_(""));
-  str.Printf("Error on line %d: %s", lineNumber, message.c_str());
+  str.Printf(wxT("Error on line %d: %s"), lineNumber, message.c_str());
 
   wxMessageDialog dlg(g_mainFrame, str, _("Error"), wxOK);
   dlg.ShowModal();
@@ -384,7 +384,10 @@ void clearPhysics(){
 void MainFrame::loadPhysics(wxString filename){
   clearPhysics();
 
-  FILE* file = fopen(filename, "r");
+  char cFilename[1024];
+  strcpy(cFilename, (const char*)filename.mb_str(wxConvUTF8));
+
+  FILE* file = fopen(cFilename, "r");
   if (file == NULL){
     loadFileError(0, _("Could not open file."));
     return;
@@ -427,7 +430,7 @@ void MainFrame::loadPhysics(wxString fil
 	if (state == 0){
 	  char name[128];
 	  sscanf(line, "%s\t", name);
-	  names[numberOfElements] = wxString(name);
+	  names[numberOfElements] = wxString::FromAscii(name);
 	  ++numberOfElements;
 	  state = 1;
 	}
@@ -467,7 +470,7 @@ void MainFrame::loadPhysics(wxString fil
 	  gravity[elementNumber] = (double)g;
 	
 	  for(int i=0;i<numberOfElements;++i){
-	    if (wxString(deathname) == names[i]){
+	    if (wxString::FromAscii(deathname) == names[i]){
 	      for (int k=0;k<100;++k){
 		death_center[elementNumber][k] = i;
 		death_prob[elementNumber] = (double)dr;
@@ -493,11 +496,11 @@ void MainFrame::loadPhysics(wxString fil
 	  int n_to = -1;
 	  int n_from = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(neighbor))
+	    if (names[i] == wxString::FromAscii(neighbor))
 	      n_neighbor = i;
-	    if (names[i] == wxString(to))
+	    if (names[i] == wxString::FromAscii(to))
 	      n_to = i;
-	    if (names[i] == wxString(from))
+	    if (names[i] == wxString::FromAscii(from))
 	      n_from = i;
 	  }
 	    
@@ -523,7 +526,7 @@ void MainFrame::loadPhysics(wxString fil
     while(fgets(line, 200, file) != NULL){
       if (line[0] == '#'){
 	//comment.
-	comment = wxString(line).Mid(1);
+	comment = wxString::FromAscii(line).Mid(1);
       }
       else if(line[0] == ' ' || line[0] == '\t' || line[0] == '\n' || line[0] == '\r'){
 	//skip
@@ -533,13 +536,13 @@ void MainFrame::loadPhysics(wxString fil
 	char* type = strtok(line, " \t\n\r");
 	if (strcmp(type, "element") == 0){
 	  char* name = strtok(NULL, " \t\n\r");
-	  names[numberOfElements] = wxString(name);
+	  names[numberOfElements] = wxString::FromAscii(name);
 	  elementDescriptions[numberOfElements] = comment;
 	  ++numberOfElements;
 	}
 	else if (strcmp(type, "group") == 0){
 	  char* name = strtok(NULL, " \t\n\r");
-	  groupNames[numberOfGroups] = wxString(name);
+	  groupNames[numberOfGroups] = wxString::FromAscii(name);
 	  ++numberOfGroups;
 	  comment = _("");
 	}
@@ -604,7 +607,7 @@ void MainFrame::loadPhysics(wxString fil
 	  
 	  int n_element = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(element))
+	    if (names[i] == wxString::FromAscii(element))
 	      n_element = i;
 	  }
 
@@ -642,7 +645,7 @@ void MainFrame::loadPhysics(wxString fil
 	  while(element != NULL){
 	    int n_element = -1;
 	    for(int i=0;i<numberOfElements;++i){
-	      if (names[i] == wxString(element))
+	      if (names[i] == wxString::FromAscii(element))
 		n_element = i;
 	    }
 
@@ -670,7 +673,7 @@ void MainFrame::loadPhysics(wxString fil
 
 	  int n_group = -1;
 	  for(int i=0;i<numberOfGroups;++i){
-	    if (groupNames[i] == wxString(group))
+	    if (groupNames[i] == wxString::FromAscii(group))
 	      n_group = i;
 	  }
 	  
@@ -687,7 +690,7 @@ void MainFrame::loadPhysics(wxString fil
 	  while(element != NULL){
 	    int n_element = -1;
 	    for(int i=0;i<numberOfElements;++i){
-	      if (names[i] == wxString(element))
+	      if (names[i] == wxString::FromAscii(element))
 		n_element = i;
 	    }
 
@@ -720,7 +723,7 @@ void MainFrame::loadPhysics(wxString fil
 	  
 	  int n_center = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(center))
+	    if (names[i] == wxString::FromAscii(center))
 	      n_center = i;
 	  }
 	  
@@ -755,7 +758,7 @@ void MainFrame::loadPhysics(wxString fil
 	    
 	    int n_trans_center = -1;
 	    for(int i=0;i<numberOfElements;++i){
-	      if (names[i] == wxString(s_trans_center))
+	      if (names[i] == wxString::FromAscii(s_trans_center))
 		n_trans_center = i;
 	    }
 	    
@@ -795,7 +798,7 @@ void MainFrame::loadPhysics(wxString fil
 	  
 	  int n_center = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(center))
+	    if (names[i] == wxString::FromAscii(center))
 	      n_center = i;
 	  }
 	  
@@ -828,9 +831,9 @@ void MainFrame::loadPhysics(wxString fil
 	  int n_center = -1;
 	  int n_neighbor = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(center))
+	    if (names[i] == wxString::FromAscii(center))
 	      n_center = i;
-	    if (names[i] == wxString(neighbor))
+	    if (names[i] == wxString::FromAscii(neighbor))
 	      n_neighbor = i;
 	  }
 
@@ -861,9 +864,9 @@ void MainFrame::loadPhysics(wxString fil
 	    int n_trans_center = -1;
 	    int n_trans_neighbor = -1;
 	    for(int i=0;i<numberOfElements;++i){
-	      if (names[i] == wxString(s_trans_center))
+	      if (names[i] == wxString::FromAscii(s_trans_center))
 		n_trans_center = i;
-	      if (names[i] == wxString(s_trans_neighbor))
+	      if (names[i] == wxString::FromAscii(s_trans_neighbor))
 		n_trans_neighbor = i;
 	    }
 
@@ -909,9 +912,9 @@ void MainFrame::loadPhysics(wxString fil
 	  int n_center = -1;
 	  int n_neighbor = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(center))
+	    if (names[i] == wxString::FromAscii(center))
 	      n_center = i;
-	    if (names[i] == wxString(neighbor))
+	    if (names[i] == wxString::FromAscii(neighbor))
 	      n_neighbor = i;
 	  }
 
@@ -941,11 +944,11 @@ void MainFrame::loadPhysics(wxString fil
 	  int n_neighbor = -1;
 	  int n_pelement = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(center))
+	    if (names[i] == wxString::FromAscii(center))
 	      n_center = i;
-	    if (names[i] == wxString(neighbor))
+	    if (names[i] == wxString::FromAscii(neighbor))
 	      n_neighbor = i;
-	    if (names[i] == wxString(pelement))
+	    if (names[i] == wxString::FromAscii(pelement))
 	      n_pelement = i;
 	  }
 
@@ -981,9 +984,9 @@ void MainFrame::loadPhysics(wxString fil
 	  int n_center = -1;
 	  int n_neighbor = -1;
 	  for(int i=0;i<numberOfElements;++i){
-	    if (names[i] == wxString(center))
+	    if (names[i] == wxString::FromAscii(center))
 	      n_center = i;
-	    if (names[i] == wxString(neighbor))
+	    if (names[i] == wxString::FromAscii(neighbor))
 	      n_neighbor = i;
 	  }
 
@@ -1008,7 +1011,7 @@ void MainFrame::loadPhysics(wxString fil
 	  //fclose(file);
 	  //return;
 	  wxString str(_(""));
-	  str.Printf("Error on line %d: Invalid line. Unrecognized keyword. Ignoring.", lineNumber);
+	  str.Printf(wxT("Error on line %d: Invalid line. Unrecognized keyword. Ignoring."), lineNumber);
 	  wxMessageDialog dlg(g_mainFrame, str, _("Error"), wxOK);
 	  dlg.ShowModal();
 	}
@@ -1209,7 +1212,7 @@ void MainFrame::OnMenu(wxCommandEvent& e
   else if(event.GetId() == 1054){
     //About
     wxString str = _("");
-    str.Printf(_("Owen Piette's Falling Sand Game\nCopyright Owen Piette 2006.\nVersion %s, compiled on %s\nCheck for updates at:\nhttp://www.piettes.com/fallingsandgame/\nThanks to coppro for his contributions.\nThanks to Troy Larson for the refresh button idea.\nThanks to purple100 for pexplosion.\nThanks to all the people at www.fallingsandgame.com for their support.\n\n"), VERSION, CVERSION);
+    str.Printf(wxT("Owen Piette's Falling Sand Game\nCopyright Owen Piette 2006.\nVersion %s, compiled on %s\nCheck for updates at:\nhttp://www.piettes.com/fallingsandgame/\nThanks to coppro for his contributions.\nThanks to Troy Larson for the refresh button idea.\nThanks to purple100 for pexplosion.\nThanks to all the people at www.fallingsandgame.com for their support.\n\n"), wxT(VERSION), wxT(CVERSION));
     wxMessageDialog dlg(this, str, _("About"));
     dlg.ShowModal();
   }

```

---

