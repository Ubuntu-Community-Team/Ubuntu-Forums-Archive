---
title: "Segmentation fault when using Shared Object"
date: 2012-04-22
forum: Programming Talk
---

### Post by jaing on 2012-04-22
I have been working on a chatbot program and yesterday decided to move the conversation engine into its own source and compile it as a shared object:

```
g++ -c -Wall -Werror -fPIC prog.cpp
g++ -shared -o libprog.so prog.o
```

The chatbot runs fine so long as I instantiate the chatbot class globally

```
chatbot chatty;
int main (int argc, char *argv[]){
     chatty.run();
     return 0;
}
```

But when I instantiate the chatbot inside main:

```
int main (int argc, char *argv[]){
     chatbot chatty;
     chatty.run();
     return 0;
}
```

It runs fine until the program ends and gives me
```
Segmentation fault
```

I have changed the code so that instead of the .so, it just #includes the source for the library and the program works fine. This is conceding defeat though.:mad:

When i run GDB it only tells me that the segmentation fault is on the close brace for main. Please help me

---

### Post by dwhitney67 on 2012-04-22
> **jaing said:**
> I have been working on a chatbot program and yesterday decided to move the conversation engine into its own source and compile it as a shared object:

```
g++ -c -Wall -Werror -fPIC prog.cpp
g++ -shared -o libprog.so prog.o
```

The chatbot runs fine so long as I instantiate the chatbot class globally

```
chatbot chatty;
int main (int argc, char *argv[]){
     chatty.run();
     return 0;
}
```

But when I instantiate the chatbot inside main:

```
int main (int argc, char *argv[]){
     chatbot chatty;
     chatty.run();
     return 0;
}
```

It runs fine until the program ends and gives me
```
Segmentation fault
```

I have changed the code so that instead of the .so, it just #includes the source for the library and the program works fine. This is conceding defeat though.:mad:

When i run GDB it only tells me that the segmentation fault is on the close brace for main. Please help me

If you are able to successfully complete the run() method using your second example (ie the one that generates the seg-fault), then I would focus your attention at the destructor for chatbot.

If you would like additional help, please post the code for chatbot.

---

### Post by jaing on 2012-04-22
> **dwhitney67 said:**
>  I would focus your attention at the destructor for chatbot.

If you would like additional help, please post the code for chatbot.

Thanks for the response! I figured that it was something to do with the destructor. It does make it through the run() function fine, and here is the class and destructor

```

class chatbot{
        public:
                chatbot();
                ~chatbot();
                void run();
                void saveChanges(bool);                 // tells the destructor if we should be keeping the changes made or not
                
        private:
                std::vector<std::string> responses;
                bool keepChanges;
};


chatbot::~chatbot(){
        std::cout << "\nShutting down...\n";
        if (keepChanges){
                std::cout << "Saving log...\n";

                // save all responses
                std::ofstream fout("responses.txt");
                int total = 0;                                    // it suddenly occurs to me that this might be a waste
                for (int ctr = 0; ctr < responses.size(); ctr++){
                        fout << responses[ctr] << std::endl;
                        std::cout << ".";
                        total++;
                }
                std::cout << "\n(" << total << ")\n";
                fout.close();

        }
        std::cout << "Finished logging.\n\n";
}
```

Thanks again.

---

