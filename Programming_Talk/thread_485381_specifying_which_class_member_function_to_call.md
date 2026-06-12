---
title: "specifying which class member function to call"
date: 2007-06-26
forum: Programming Talk
---

### Post by spamalot on 2007-06-26
hi all,

any thoughts on the pros and cons of A vs AA (compile, run time, debugging...) in the context of a larger program (for example multiple template parameters)?


class B{
	public:
	 double arbitrary_name(){return 0;};	
};
template<class T> class A{
	public:
	 A(T& b_,double (T::*)());	
	 double f();
	private:
		T& b;	
		double (T::*mf)();	
};
template<class T> A<T>::A(T& b_,double (T::*mf_)()):b(b_),mf(mf_){};
template<class T> double A<T>::f(){return (b.*mf)();};
template<class T,double (T::*)()> class AA{
	public:
	 AA(T& b_);	
	 double f();
	private:
		T& b;	
};
template<class T,double (T::*mf_)()> AA<T,mf_>::AA(T& b_):b(b_){};
template<class T,double (T::*mf_)()> double AA<T,mf_>::f(){return (b.*mf_)();};


B b;
A<B> a(b,&B::arbitrary_name);
AA<B,&B::arbitrary_name> aa(b);

---

