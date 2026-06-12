---
title: "friend functions"
date: 2008-05-02
forum: Programming Talk
---

### Post by StOoZ on 2008-05-02
Im having some issues, from my understanding , a friend function doesnt really belong to the class,its not a part of the object , but , can access private data, seems like, it doesnt really access the private data, for example:
> template<typename T>
class BASE
{
private:
    char* name;
public:
    BASE():name("regular template") {}
    void show(void){
        cout<<name<<endl;
    }
    friend void babon(void);
};

void babon(void){
    cout<<name<<"Friend called\n";
}


as you can see, the private var 'name' is called in the friend funtion, but I still getting an error which claims that it was not declared in that scope.
any idea?

---

### Post by Npl on 2008-05-02
> **StOoZ said:**
> as you can see, the private var 'name' is called in the friend funtion, but I still getting an error which claims that it was not declared in that scope.
any idea?Well, you need an Class-Instance to use its (private) members.```
template<typename T>
class BASE
{
private:
char* name;
public:
BASE():name("regular template") {}
void show(void){
cout<<name<<endl;
}
friend void babon(BASE&);
};

void babon(BASE& obj){
cout<<obj.name<<"Friend called\n";
}
```

---

