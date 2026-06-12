---
title: "Silly question on wxWindowID"
date: 2008-12-07
forum: Programming Talk
---

### Post by Jonas thomas on 2008-12-07
Hi this is a dumb question.

Can someone point me to the "official" documentation on exactly to the design intent of "wxWindowID"?  I'm still somewhat newbish on this wxwidgets stuff and I'm sort or tearing my hair out here.  I'm not quite sure how to ask the question of a browser. I'm getting thousands of hits of what it is, but how do I find what it does?  I"m trying go through item by item through the wxFrame constructor so it's clear in my head what's going on.

    wxFrame *New(wxWindow *parent,
                 wxWindowID winid,
                 const wxString& title,
                 const wxPoint& pos = wxDefaultPosition,
                 const wxSize& size = wxDefaultSize,
                 long style = wxDEFAULT_FRAME_STYLE,
                 const wxString& name = wxFrameNameStr);

[http://docs.wxwidgets.org/stable/wx_wxframe.html]("http://docs.wxwidgets.org/stable/wx_wxframe.html")
Refers to it as "The window identifier."

[Edit] I'm still a little fuzzy on the wxWindowID stuff but I think I found some stuff that might clear it up a little bit for me:[http://docs.wxwidgets.org/stable/wx_stdevtid.html#stdevtid]("http://docs.wxwidgets.org/stable/wx_stdevtid.html#stdevtid")
> 
Standard event identifiers

wxWidgets defines a special identifier value wxID_ANY which is used in the following two situations:

    * when creating a new window you may specify wxID_ANY to let wxWidgets assign an unused identifier to it automatically
    * when installing an event handler using either the event table macros or wxEvtHandler::Connect, you may use it to indicate that you want to handle the events coming from any control, regardless of its identifier 

Another standard special identifier value is wxID_NONE: this is a value which is not matched by any other id.

wxWidgets also defines a few standard command identifiers which may be used by the user code and also are sometimes used by wxWidgets itself. These reserved identifiers are all in the range between wxID_LOWEST and wxID_HIGHEST and, accordingly, the user code should avoid defining its own constants in this range.

Perhap's this will become more clear to me once, I work through some more code samples..

---

