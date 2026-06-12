---
title: "wxWidgets examples on Intrepid - anyone got the same error?"
date: 2009-03-27
forum: Programming Talk
---

### Post by Zugzwang on 2009-03-27
Hi all,

I'm trying to compile some examples from the package "wx2.8-examples" in Ubuntu Intrepid. Most of them compile well, but the "dataview" throws errors. Here's what I get when typing "make" in the directory where I unpacked that example (using the script provided):

```

g++ -c -o dataview_dataview.o -I.  `wx-config --cxxflags`   -MTdataview_dataview.o -MF`echo dataview_dataview.o | sed -e 's,\.o$,.d,'` -MD dataview.cpp                                                                                                                                     
dataview.cpp:42: error: expected class-name before ‘{’ token                                                                                  
dataview.cpp:140: error: expected class-name before ‘{’ token                                                                                 
dataview.cpp:169: error: ‘wxDataViewListModel’ has not been declared                                                                          
dataview.cpp: In constructor ‘MyCustomRenderer::MyCustomRenderer()’:                                                                          
dataview.cpp:143: error: class ‘MyCustomRenderer’ does not have any field named ‘wxDataViewCustomRenderer’                                    
dataview.cpp:143: error: ‘wxDATAVIEW_CELL_ACTIVATABLE’ was not declared in this scope                                                         
dataview.cpp: At global scope:                                                                                                                
dataview.cpp:185: error: expected class-name before ‘{’ token                                                                                 
dataview.cpp: In member function ‘void MyUnsortedTextModel::AppendRow(const wxString&)’:                                                      
dataview.cpp:233: error: ‘RowAppended’ was not declared in this scope                                                                         
dataview.cpp: In member function ‘void MyUnsortedTextModel::PrependRow(const wxString&)’:                                                     
dataview.cpp:239: error: ‘RowPrepended’ was not declared in this scope                                                                        
dataview.cpp: In member function ‘void MyUnsortedTextModel::InsertRowAt1(const wxString&)’:                                                   
dataview.cpp:245: error: ‘RowInserted’ was not declared in this scope                                                                         
dataview.cpp: In member function ‘void MyUnsortedTextModel::DeleteRow(unsigned int)’:                                                         
dataview.cpp:251: error: ‘RowDeleted’ was not declared in this scope                                                                          

```

---

