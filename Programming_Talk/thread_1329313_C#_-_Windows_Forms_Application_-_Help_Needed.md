---
title: "C# - Windows Forms Application - Help Needed"
date: 2009-11-17
forum: Programming Talk
---

### Post by hey_ram on 2009-11-17
Hi all,

I have been working on a simple GUI application in C# using Visual Studio 2005. I have never programmed in C# before and do not know what to make of the errors. Any help would be most appreciated.

Problem:
To change the node IDs of sensors in an embedded system. This will help in debugging purposes.

Implementation:
A GUI with 2 fields, one for entering the OriginalNodeID and the other for entering the NewNodeID. Two buttons, one for "Enter" and the other for "Cancel". I am facing a problem in supplying the values to the variables from the GUI. The function for "Enter", that I have written so far is:

```

private: System::Void Enter_Click(System::Object^  sender, System::EventArgs^  e) 
     {
	/*The function to execute when "Enter" is pressed. Steps:
	1. Check if entries in both fields are numbers. If not, reject.
	2. If the entries are both numbers, proceed.
	3. Check if original node ID is present among the node ID lists.
	4. Check if node ID to change to does not clash with an existing node ID.
	5. If all is good till now, then change the node ID and proceed.
	*/

	//Step 1: Check if both entries are integers.
	System::Int32^ OriginalNodeID;
	System::Int32^ NewNodeID;   //the 2 nodes.
			 			 
	OriginalNodeID->TryParse(OriginalNodeID_Box->Text, OriginalNodeID);
	NewNodeID->TryParse(NewNodeID_Box->Text, NewNodeID);
    }
```

The errors that I get are as follows:
C2664: 'bool System::Int32::TryParse(System::String ^,int %)' : cannot convert parameter 2 from 'System::Int32 ^' to 'int %'

This error is flagged in both lines where I try to use the function TryParse.

Any help on this would be most appreciated. I have tried looking at various other forums and on the net, but have not had much luck so far.

Thanks.

---

### Post by arubislander on 2009-11-17
Hi,

First off, you do know that your code is in C++ right?

Anyhow: The compiler wants you to declare OriginalNode and NewNode as 'int %' instead of 'int ^' as you are declaring them now.

---

### Post by hey_ram on 2009-11-24
hi,

thanks for your reply and apologies for not having replied earlier. i was able to figure that problem out. 

I have the code for the application and am required to write a troubleshooting/diagnostic tool. I think I have a fair idea of where in the code this snippet will go, but I am unsure about calling a GUI (the tool must be GUI based) from this program that is not main.

My questions are as follows:
1. How to call a GUI from a program that is not main()?
2. How can I make sure that the values entered in from the GUI and the variables in the program itself will be visible to each other?

P.S: I may not be able to post the whole code. It might be proprietary.

Any help is most welcome.
Thanks,

---

### Post by arubislander on 2009-12-02
I'm not sure I understand the question. Are you writing a WinForms application? Or are you writing an application that has to call a WinForms application? Or is your question related to accessing a UserControl from the Main() function? If the latter is the case, then I'm not sure you are going about it in the right way...

So maybe if you could be a little more precise in what it is you are trying to achieve, I might be able to give some pointers.

BTW are you using Mono or MS .NET Framework?

---

