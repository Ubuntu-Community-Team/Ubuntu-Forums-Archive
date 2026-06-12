---
title: "MonoDevelop 1.0 Command Line Input"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by TomDaBomb2u on 2008-05-13
I'm having a problem with MonoDevelop: I cannot figure out how to input data when I've called a cin statement. 

I've entered```
cout << "Enter a phrase";
cin >> phrase;
```and cannot figure where to type in my input.

I've looked for forums specifically on MonoDevelop and haven't found one. If I'm in the wrong place, please someone tell me where I can find help. If you CAN help, please do! :-)

Thanks!
-Thomas

---

### Post by Cypher on 2008-05-13
MonoDevelop is a C# IDE, what you're doing is C++. You'd do something like the following in MonoDevelop and C#
[CODE]
using system

class Hello
{
    [STAThread]
    static void main(string[] args)
    {
        string phrase;

        Console.Write("Enter a phrase: ");
        phrase = Console.ReadLine;

        Console.WriteLine(); // Put a newline

        Console.WriteLine("You entered: {0}", phrase);
    }
}

---

### Post by TomDaBomb2u on 2008-05-13
Thanks for the reply. MonoDevelop also works as a C++ compiler. I got the program to compile fine, I just can't figure out where to enter my input.

---

### Post by desturrr on 2009-05-10
i recently installed the monodevelop on my ubuntu for cpp applications , when i try to compile , it compile just fine, but using the cin to get input from the user is not working , simply : 

int main() {
    int x=0;
    cout<<"Something to test cout";
    cin>>x;
    cout<<x;
 return 0;
}

it doesn't wait for input , the result is : Something to test cout 0 , i dont get it ... where is the problem...why it is  just skipping the cin part??

thankss in advance...

---

### Post by ionizedwarhead on 2011-01-16
Reviving up threads :D but I have the answer! and I want to be helpful n.~

After making a solution...

What you do is in MonoDevelop under project on your menu bar at the top, select  the very last option in that drop down box so it'll be <solution name> Options. Then on the left you'll see different bolded categories in a file browser kind of setting...look under the one that says Run and there will be a topic called general. 

Now you should see a little check box that says run in external console check it and you are good to go :D the console will wait for your input when you call for it^^

Hope you guys found it helpful :D (Well at any rate I would have if this had been here when I was forum scrounging :))

---

