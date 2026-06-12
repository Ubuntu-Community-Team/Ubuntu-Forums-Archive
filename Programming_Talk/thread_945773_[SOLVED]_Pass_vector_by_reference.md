---
title: "[SOLVED] Pass vector by reference"
date: 2008-10-12
forum: Programming Talk
---

### Post by kjohansen on 2008-10-12
I am doing a machine learning project that is going to involve large vectors.

I want to pass a vector by reference into a class and assign a class variable to this reference.

Class prototype from header file:
[php]
    class SMO
    {
    private:
      
        ...

        vector<vector<float> > x;
        vector<float> y;

         ... 
        
    public:
        SMO(float,float,float,float,float);
        void AddDataPoints(vector<float>&,vector<float>&,bool);
        bool Train();
        float Predict(vector<float>);
    };
[/php]


Function from class definition:
[php]
void SMO::AddDataPoints(vector<float>& x_in,vector<float>& y_in,bool clear=true)
{
    if(clear)
    {
        x=x_in;
        y=y_in;
    }
}
[/php]

I get an error that says there is no match for operator=.

Any ideas.

EDIT:  Stupid me, I realized the problem as I hit submit.  I have a vector<float>  and a vector<vector<float> >.

---

### Post by dwhitney67 on 2008-10-12
> **kjohansen said:**
> I am doing a machine learning project that is going to involve large vectors.

I want to pass a vector by reference into a class and assign a class variable to this reference.

Class prototype from header file:
[php]
    class SMO
    {
    private:
      
        ...

        vector<vector<float> > x;
        vector<float> y;

         ... 
        
    public:
        SMO(float,float,float,float,float);
        void AddDataPoints(vector<float>&,vector<float>&,bool);
        bool Train();
        float Predict(vector<float>);
    };
[/php]


Function from class definition:
[php]
void SMO::AddDataPoints(vector<float>& x_in,vector<float>& y_in,bool clear=true)
{
    if(clear)
    {
        x=x_in;
        y=y_in;
    }
}
[/php]

I get an error that says there is no match for operator=.

Any ideas.

EDIT:  Stupid me, I realized the problem as I hit submit.  I have a vector<float>  and a vector<vector<float> >.

I hope you solved the compile problem.  The error that you originally received had nothing to do with the vector; it had to do with your assignment to the parameter "clear" in the implementation of your method.  If you want to setup a default value for a parameter, it must be done in the method declaration, not the implementation.

---

