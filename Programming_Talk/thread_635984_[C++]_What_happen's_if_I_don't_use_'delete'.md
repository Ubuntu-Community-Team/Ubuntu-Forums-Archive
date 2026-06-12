---
title: "[C++] What happen's if I don't use 'delete'?"
date: 2007-12-09
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2007-12-09
Let's say I have a function which declares a pointer to a class and assigns to it an instance of this class using "new". Then the code in the function uses the class in various ways and then exits without deleting the pointer using "delete".

What happens if I call this function 5 times memory-wise? Will the previous 4 instances still exist. If yes, will the memory used for these still be connected to my program? If yes, does that mean if I call my function n-times it will eat up all the memory available?

---

### Post by aks44 on 2007-12-09
> **SledgeHammer_999 said:**
> What happens if I call this function 5 times memory-wise? Will the previous 4 instances still exist. If yes, will the memory used for these still be connected to my program? If yes, does that mean if I call my function n-times it will eat up all the memory available?

Yes, yes and yes.

While your program is running, you HAVE to manage memory, period. When it ends however, the system will (fortunately) reclaim all the memory allocated by your program.

Another problem when not calling delete is that the destructor of your class won't be called, which is unacceptable in the vast majority of the cases.

A trick to help you manage memory more easily is to use smart pointers (std::auto_ptr, boost::shared_ptr, ...). This way you won't have to think about calling delete, the RAII mechanism will take care of that for you. Plus it is the bare minimum to make your code exception-safe.

---

### Post by Martin Witte on 2007-12-09
you don't release your memory, at least as long as your app runs, and on certain os it will never return the memory

---

### Post by Lster on 2007-12-09
The Wikipedia article may be useful:

[http://en.wikipedia.org/wiki/Memory_leak](http://en.wikipedia.org/wiki/Memory_leak)

---

### Post by SledgeHammer_999 on 2007-12-09
Well I have a problem where if I call delete then nothing happen's. It is wxwidgets' related. I already posted there but I have no answer so far. Here is my post: > Hello I am a n00b in C++ programming so try to bear with me.

I am going to give a simple example of my "question-problem":

Let's say you have 2 wxFrame called Frame1 and Frame2.
In Frame1 you have a wxButton which, when clicked, hides Frame1 and shows Frame2 with this code:
wxwidgets:
void Frame1::OnButton2Click(wxCommandEvent& event)
{
    Frame2* fr2 = new Frame2(this);
    fr2->previousfr = this; //pass handler to this instance of Frame1
    fr2->Show();
    Show(false);
}


Frame2 contains some things which ,when used, increase the memory used by the program(such as listbox,textcrtl). It also contains another wxButton which, when clicked, shows Frame1 and closes Frame2 with this code:
wxwidgets:
void Frame2::OnGoBackClick(wxCommandEvent& event)
{
    previousfr->Show(); //this handler points to the instance of Frame1 which called Frame2
    Close();
}


My question is, is this a good practice for memory management? When I Close() Frame2 does it release it's memory?(well gnome's system monitor indicates that no)
I know I am suppose to delete fr2 but I don't know when and how.If I put "delete fr2" after "Show(false)" Frame2 doesn't even appear.
Is there some other way I should do what my code does now?

I am concerned about this because when I show Frame1 the user might click again the button and create another instance of Frame2 which in turn will use additional memory(probably) if the previous instance "still exists and holds memory for itself"

thank you in advance.


Do you have any wxWidgets's experience to help me?
I read a little the docs and Destroy() might do what delete does. And also they don't recommend using delete to destroy a window.
Can a class in fact release the memory used for itself?( I suppose this is what Destroy() does)

thank you for your answers and I hope you keep them coming.

---

### Post by aks44 on 2007-12-09
> **SledgeHammer_999 said:**
> Well I have a problem where if I call delete then nothing happen's.

Ok, I don't have any wxWidget specific experience, but there are a couple of solutions to this. My best bet would be something like this:

```
class Frame1: public wxWhatever
{
private:
  Frame2* m_frame2;
  /*...*/
public:
  Frame1();
  ~Frame1();
};

Frame1::Frame1()
  : m_frame2(0)
{
  /*...*/
}

void Frame1::OnButton2Click(wxCommandEvent& event)
{
  if (!m_frame2)
    m_frame2 = new Frame2(this);
  m_frame2->previousfr = this;
  m_frame2->Show();
  Show(false);
}

Frame1::~Frame1()
{
  if (m_frame2)
    m_frame2->Destroy();
  /*...*/
}
```

This way you'll create only one instance of Frame2, next time it will be reused.

> **SledgeHammer_999 said:**
> Can a class in fact release the memory used for itself?( I suppose this is what Destroy() does)
Yes

---

### Post by SledgeHammer_999 on 2007-12-09
From what I see (in your example) you don't need to use delete. You use Destroy() instead. Then I have no problem. On my frame2 code I'll check when it is closed(frame2) and call Destroy().

If this is done correctly, will the memory usage of my app on "systems monitor" drop instantly? Or after some time?

---

### Post by aks44 on 2007-12-09
> **SledgeHammer_999 said:**
> From what I see (in your example) you don't need to use delete. You use Destroy() instead. Then I have no problem.

Don't get me wrong, I used Destroy() because *you* stated that the wx docs advise it over delete. ;) Other than that I'd have used delete... (but as I said, I don't have any wx experience).


Now as far as your application's memory usage goes, I doubt that it will drop down. Usually C++ doesn't give (small blocks of) memory back to the system, but to its own memory manager so that the next allocation will be faster. But at least, next time you allocate something it won't take *more* memory from the system... :)

---

### Post by SledgeHammer_999 on 2007-12-09
thank you very much for your explanation about memory usage. Apparently Destroy() is the correct way because when I create another instance of frame2(after destroying the first instance) and fill it with data(a listbox to be correct) the memory usage doesn't go up instantly.

thank you. I think it is solved.

---

### Post by archivator on 2007-12-09
Just to quote the docs on this: > **~wxWindow()**

Destructor. Deletes all subwindows, then deletes itself. **Instead of using the delete operator explicitly, you should normally use wxWindow:: Destroy** so that wxWidgets can delete a window only when it is safe to do so, in idle time.

---

