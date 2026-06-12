---
title: "Getting stuck in"
date: 2011-07-10
forum: Programming Talk
---

### Post by olie440 on 2011-07-10
Hi,

I have been trying to get stuck into open source software by trying to add a simple patch to empathy to make it send files when draged and dropped, but i cant seam to get this working:

```
static void
chat_window_paste_activate_cb (GtkAction         *action,
			       EmpathyChatWindow *window)
{
	EmpathyChatWindowPriv *priv;

	g_return_if_fail (EMPATHY_IS_CHAT_WINDOW (window));

	priv = GET_PRIV (window);
	// my code starts here
	
	//get clipboard content
	char clipboardfile[256] = gtk_clipboard_get (GDK_SELECTION_CLIPBOARD);
	
	//find any occurance of file:// which means a user draged a file to the window
	int clipboardfilefound = strstr(clipboardfile, "file://");
	
	clipboardfile = g_file_get_uri (clipboardfile);
	
	// if they are occurences of "file://" then send file else paste text
	if(clipboardfilefound != NULL) {
		
		  gtk_recent_manager_add_item (recent_manager, clipboardfile);
		
	}else{
	//end of my code 
	
	empathy_chat_paste (priv->current_chat);
	
// end of the IF i inserted	
}
}
```

Can anyone who knows empathy help me with this

btw this is applyed to empathy-chat-window.c at line 1109

---

