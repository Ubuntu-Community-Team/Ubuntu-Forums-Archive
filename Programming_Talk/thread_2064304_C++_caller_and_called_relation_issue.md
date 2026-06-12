---
title: "C++ caller and called relation issue"
date: 2012-09-28
forum: Programming Talk
---

### Post by pellyhawk on 2012-09-28
I am developing a test program using visual studio running on  windows to test a application software running on arm-linux platform.

I need to create 3 tab windows and found some source code. I noticed CFrameWnd::OnCreateClient and CFrameWnd::OnCreate and did not found out CFrameWnd::OnCreate calls CFrameWnd::OnCreateClient. But in msdn, it tells me that CFrameWnd::OnCreateClient "Called by the framework during the execution of OnCreate." 

Where can I find out this call by framework? Is this call encapsulated by MFC and  thus we cannot see it?

---

### Post by mdurham on 2012-09-29
I think you are talking about using MFC's but this is a Linux forum. You should ask MFC questions in a Windows forum.

---

