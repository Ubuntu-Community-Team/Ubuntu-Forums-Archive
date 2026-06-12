---
title: "got myself confused on accessing the internal elements of an object via an iterator."
date: 2011-03-26
forum: Programming Talk
---

### Post by Jonas thomas on 2011-03-26
I seem to be missing something obvious...
I found an object within a vector list and I want to pass the pointer for that object to be able to work on the internals for that object.

It seems like I should be able to do this but I've been knocking my head against the wall trying to get this to work.
If some one could point out (pun intended) where I'm going wrong I'd appreciate it.

Class declarations
```
class timeCard
{
     time24 clock_in();
     time24 clock_out();

};
class weeklyLabor
{
public:
private:
    vector<timeCard> tcards;//Really there should be a time date stamp in this.
};
class employee
{
    private:
    string nameFirst;
    string nameLast;
    string ssn;
    float hourlyPayRate;
    vector<weeklyLabor> weekLabor;
    public:

	 bool operator==(const employee&);
	 employee(string Ssn="",string nameL="",string nameF="",float PayRate=0);
     string getSsn(void);
	 friend istream & operator>>(istream &istr, employee & p);
     friend ostream & operator<<(ostream &ostr, employee & p);

};



 class payroll
{
    public:

    payroll();
    vector <employee> emp;


	void employeeEnterLabor(const employee& empLaborTicket);
	void employeeHire(const employee& newHire);
	void employeeFire(employee  EmpFire);


	void displayAllEmployeeData();
    void readWeeklyPayrollFile(string fileName);
    private:
};
```

Things go south here:
```
void payroll::employeeEnterLabor(const employee & empLabor )
{


 	vector <employee>::iterator itr;
	itr= find(emp.begin(),emp.end(),empLabor);
	if (itr !=emp.end())//Employee exists need to add the labor
    {
[B]        //I'm stuck here.
        employee *ptrEmp;
        ptrEmp =*itr;// This doesn't work.
[/B]
    }
	else
	{
		throw rangeError("Attempt to enter labor for an employee who doesn't exist");
	}


```

I'm thinking that I probably need to overload an operator within the object to return *this.  Is there a more direct way to do this without an operator overload?

---

### Post by dwhitney67 on 2011-03-26
(scratch my initial reply)

The vector is a collection of employee objects; thus you require something like:
```

employee& refEmp = *itr;

```
This will offer you a reference to the object stored in the vector.

---

### Post by Jonas thomas on 2011-03-26
> **dwhitney67 said:**
> (scratch my initial reply)

The vector is a collection of employee objects; thus you require something like:
```

employee& refEmp = *itr;

```
This will offer you a reference to the object stored in the vector.

Hmm looks different and... it works... Need to sit back and meditate on this for a while.
Although now I don't have access to the private members (which makes sense I think.....) so I can get around that with couple of public member function.
Thanks...
I was banging my head against the wall on that one for a couple of hours.

---

### Post by Jonas thomas on 2011-03-26
opps... double post

---

