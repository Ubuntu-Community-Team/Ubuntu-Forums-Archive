---
title: "Operator ="
date: 2011-09-05
forum: Programming Talk
---

### Post by roadkillguy on 2011-09-05
I'm working on some generic c++ code. Basically I have a Network class that has a few vectors (lists) of pointers. (Nodes and Connections) When operator= is called, the Networks need to copy one another by creating classes of their own while still maintaining the proper structure of the other Network.

The problem is, when a Network class (not Network *) is passed in to the operator=() function, it is destroyed when the function is finished.  When it is destroyed, it deletes those pointers in the lists and leaves the actual instance passed in to delete them again which causes a glibc error.

Simplified Example:

```
class Network
{
  public:

    Connection * foo;

    Network()
    {
        foo = new Connection();
    }
    ~Network()
    {
        delete foo;
    }
    Network::operator=(Network _network)
    {
        //DO some other stuff with the other subclasses not included in this example.
    }
};

int main()
{
    Network network1;
    Network network2;
    network1 = network2;  //The copy of network2 is deleted, and leaves network2 to attempt to delete foo again at the end of main()
    
    return 0;
}

OUTPUT:
*** glibc detected *** ./nGen: double free or corruption (!prev): 0x09cefd18 You're a terrible programmer***

Pointers that I don't really see the point in...
```

This is what I believe causes it.  The values within the class must be pointers for the subclasses to rely on.  I'm not sure how to solve this.

---

### Post by karlson on 2011-09-05
> **roadkillguy said:**
> 
The problem is, when a Network class (not Network *) is passed in to the operator=() function, it is destroyed when the function is finished.  When it is destroyed, it deletes those pointers in the lists and leaves the actual instance passed in to delete them again which causes a glibc error.



Right....

> **roadkillguy said:**
> 
This is what I believe causes it.  The values within the class must be pointers for the subclasses to rely on.  I'm not sure how to solve this.

First off foo should be private.  Second, The operator='s signature is:
<class> &operator=(const <class> &src) { ... ; return *this }
```

class Network
{
  private:
    Connection *foo;
  public:
    Network()
    {
        foo = new Connection();
    }
    ~Network()
    {
        delete foo;
    }
    Network &operator=(const Network &_network)
    {
        // Do Stuff

        return *this;
    }
};

```

May be you should inherit Network From Connection as it appears that Network class is a connection.  You should learn and understand C++'s pass by reference.

---

### Post by roadkillguy on 2011-09-05
That was a simplified example to illustrate the deletion of connection.  This is the real thing (Network.h):

```


class Network
{
	std::vector<InputNeuron *> m_inputList;
	std::vector<OutputNeuron *> m_hiddenList;
	std::vector<OutputNeuron *> m_outputList;
	
	std::vector<Connection *> m_connectionList;

  public:

	Network(int _inputNum = -1, int _hiddenNum = -1, int _outputNum = -1);
	~Network();
	
	void init(int, int, int);
	void clear();
	
	void update();
	
	Network operator=(Network);
        //TONS MORE FUNCTIONS...
}
```

After operator= is called, the pointers in those vectors are deleted.

Ahh arguments by reference is different than arguments by address.  So the & will solve the problem here?

EDIT: I didn't know you could do that.  Problem solved.

Thanks!

---

### Post by dwhitney67 on 2011-09-05
The thread is marked as solved, however this is still incorrect:
```

Network operator=(Network);

```
It should be:
```

Network**&** operator=(**const** Network& other);

```
The operator=() presumably will modify the underlying 'this' instance, and thus the necessity to return 'this' by reference; the original definition above returns a copy of 'this', which is incorrect.

Recompile your original code with the **-Weffc++** compiler option enabled so that you see the warning.

---

### Post by karlson on 2011-09-05
> **roadkillguy said:**
> That was a simplified example to illustrate the deletion of connection.  This is the real thing (Network.h):

```


class Network
{
	std::vector<InputNeuron *> m_inputList;
	std::vector<OutputNeuron *> m_hiddenList;
	std::vector<OutputNeuron *> m_outputList;
	
	std::vector<Connection *> m_connectionList;

  public:

	Network(int _inputNum = -1, int _hiddenNum = -1, int _outputNum = -1);
	~Network();
	
	void init(int, int, int);
	void clear();
	
	void update();
	
	Network operator=(Network);
        //TONS MORE FUNCTIONS...
}
```

After operator= is called, the pointers in those vectors are deleted.

Ahh arguments by reference is different than arguments by address.  So the & will solve the problem here?

EDIT: I didn't know you could do that.  Problem solved.

Thanks!

I would suggest that before you do any other coding you read some or all of the following:

[http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X/ref=pd_sim_b_12](http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X/ref=pd_sim_b_12)
[http://www.amazon.com/C-Programming-Language-Special/dp/0201700735/ref=sr_1_2?s=books&ie=UTF8&qid=1315244287&sr=1-2](http://www.amazon.com/C-Programming-Language-Special/dp/0201700735/ref=sr_1_2?s=books&ie=UTF8&qid=1315244287&sr=1-2)
[http://www.amazon.com/Inside-Object-Model-Stanley-Lippman/dp/0201834545/ref=sr_1_1?s=books&ie=UTF8&qid=1315244233&sr=1-1](http://www.amazon.com/Inside-Object-Model-Stanley-Lippman/dp/0201834545/ref=sr_1_1?s=books&ie=UTF8&qid=1315244233&sr=1-1)
[http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=pd_bxgy_b_text_b](http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=pd_bxgy_b_text_b)
[http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=pd_bxgy_b_img_b](http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=pd_bxgy_b_img_b)

---

### Post by roadkillguy on 2011-09-05
> **dwhitney67 said:**
> The thread is marked as solved, however this is still incorrect:
```

Network operator=(Network);

```
It should be:
```

Network**&** operator=(**const** Network& other);

```
The operator=() presumably will modify the underlying 'this' instance, and thus the necessity to return 'this' by reference; the original definition above returns a copy of 'this', which is incorrect.

Recompile your original code with the **-Weffc++** compiler option enabled so that you see the warning.

Me? or karlson?  Is '*this' incorrect?

The second chunk of code I posted was BEFORE the final product.  I understand what's going on.  My problem is solved.  No more memory issues.

---

### Post by karlson on 2011-09-05
> **roadkillguy said:**
> Me? or karlson?  Is '*this' incorrect?


This is precisely why I recommended you read the books before you continue doing coding in C++.

The code you posted had operator= as:
```

Network operator=(Network)

```

This is wrong by in more ways then one.

1.  You are creating a copy of the argument before doing any manipulation
2.  when you return you are making another copy of the Network object instance.

Also.  The reason that you don't have problems with the last code you posted is that destructor destroys the vectors not the underlying pointers stored in them.  If you were to do a complete clean up you will have problems as before.

> 
The second chunk of code I posted was BEFORE the final product.  I understand what's going on.  My problem is solved.  No more memory issues.

If the code anything like what you posted all you have is a different memory problem.  The memory leak.

---

### Post by roadkillguy on 2011-09-05
This is my header:

```
class InputNeuron : public Neuron
{
  public:

	InputNeuron(int);
	
	void setValue(float);
};

class OutputNeuron : public Neuron
{
	std::vector<Connection *> m_inputList;

  public:

	OutputNeuron(int, int);
	
	void update();
	
	void addInput(Connection *);
	void clearInputs();
};

class Network
{
	std::vector<InputNeuron *> m_inputList;
	std::vector<OutputNeuron *> m_hiddenList;
	std::vector<OutputNeuron *> m_outputList;
	
	std::vector<Connection *> m_connectionList;

  public:

	Network(int _inputNum = -1, int _hiddenNum = -1, int _outputNum = -1);
	~Network();
	
	void init(int, int, int);
	void clear();
	
	void update();
	
	Network & operator=(Network &);
        //TONS MORE FUNCTIONS...
}
```

This is my implementation of the functions shown.
```
Network::Network(int _inputNum, int _hiddenNum, int _outputNum)
{
	if(_inputNum != -1 && _hiddenNum != -1 && _outputNum != -1)
	{
		init(_inputNum, _hiddenNum, _outputNum);
	}
}
Network::~Network()
{
	clear();
}

void Network::init(int _inputNum, int _hiddenNum, int _outputNum)
{
	int i;
	
	for(i = 0;i < _inputNum;i ++)
	{
		m_inputList.push_back(new InputNeuron(i));
	}
	
	for(i = 0;i < _hiddenNum;i ++)
	{
		m_hiddenList.push_back(new OutputNeuron(i, NEURONTYPE_HIDDEN));
	}
	
	for(i = 0;i < _outputNum;i ++)
	{
		m_outputList.push_back(new OutputNeuron(i, NEURONTYPE_OUTPUT));
	}
}
void Network::clear()
{
	int count = 0;
	
	while(!m_inputList.empty())
	{
		delete m_inputList.back();
		m_inputList.pop_back();
	}
	
	while(!m_hiddenList.empty())
	{
		delete m_hiddenList.back();
		m_hiddenList.pop_back();
	}
	
	while(!m_outputList.empty())
	{
		delete m_outputList.back();
		m_outputList.pop_back();
	}
	
	while(!m_connectionList.empty())
	{
		delete m_connectionList.back();
		m_connectionList.pop_back();
	}
}

void Network::update()
{
	vector<OutputNeuron *>::iterator it;
	
	for(it = m_hiddenList.begin();it < m_hiddenList.end();it ++)
	{
		(*it)->update();
	}
	for(it = m_outputList.begin();it < m_outputList.end();it ++)
	{
		(*it)->update();
	}
}

Network & Network::operator=(Network & _network)
{
	int i;
	
	clear();
	init(_network.getInputNum(), _network.getHiddenNum(), _network.getOutputNum());
	
	for(i = 0;i < _network.getConnectionNum();i ++)
	{
		Connection * connection = _network.getConnection(i);
		
		Neuron * eqvInput; //EQUIVALENT INPUT NEURON TO THE CONNECTION
		if(connection->getInput()->getType() == NEURONTYPE_INPUT)
		{	
			eqvInput = getInputNeuron(connection->getInput()->getIndex());
		}
		else if(connection->getInput()->getType() == NEURONTYPE_HIDDEN)
		{
			eqvInput = getHiddenNeuron(connection->getInput()->getIndex());
		}
		else if(connection->getInput()->getType() == NEURONTYPE_OUTPUT)
		{
			eqvInput = getOutputNeuron(connection->getInput()->getIndex());
		}
		
		OutputNeuron * eqvOutput; //EQUIVALENT OUTPUT NEURON TO THE CONNECTION
		
		//INPUTS TO THE NETWORK ARE NEVER AN OUTPUT TO A CONNECTION
		if(connection->getOutput()->getType() == NEURONTYPE_HIDDEN)
		{
			eqvOutput = getHiddenNeuron(connection->getOutput()->getIndex());
		}
		else if(connection->getOutput()->getType() == NEURONTYPE_OUTPUT)
		{
			eqvOutput = getOutputNeuron(connection->getOutput()->getIndex());
		}
		
		Connection * final = addConnection(eqvInput, eqvOutput, connection->getWeight(), connection->getType());
	}
	
	return *this;
}
```

In post #3 I posted my old code to clarify what I was doing and then half way through updated it to this (Which fixed it) and I marked it as solved.  I apologize if that caused confusion.

---

### Post by dwhitney67 on 2011-09-05
I'm curious... what does the following function do, and why do you care about the return value?  (You don't seem to use it).
```

**Connection * final** = addConnection(eqvInput, eqvOutput, connection->getWeight(), connection->getType());

```

P.S.  If you have no intention of modifying _network within operator=(), then declare it as a const reference.

---

### Post by karlson on 2011-09-05
@dwhitney67
The code needs "Effective C++", "More Effective C++" and a few other C++ books but I'll let it be since I am not the one writing it and hopefully not the one using it....

---

### Post by roadkillguy on 2011-09-06
> **dwhitney67 said:**
> I'm curious... what does the following function do, and why do you care about the return value?  (You don't seem to use it).
```

**Connection * final** = addConnection(eqvInput, eqvOutput, connection->getWeight(), connection->getType());

```

P.S.  If you have no intention of modifying _network within operator=(), then declare it as a const reference.

Connection * final was for debugging purposes.  I should take that out...

Is there any reason you would be modifying the input to operator=?  I suppose I should use const more.

```
Network.cpp:140: error: passing &#8216;const Network&#8217; as &#8216;this&#8217; argument of &#8216;int Network::getInputNum()&#8217; discards qualifiers
```

Not sure what to do at this point.  What's wrong with calling a member function of a const class?

> The code needs "Effective C++", "More Effective C++" and a few other C++ books but I'll let it be since I am not the one writing it and hopefully not the one using it....

I've been coding c++ for just under a year... please point out to me what's wrong.

---

### Post by karlson on 2011-09-06
With respect to your last question:

> **roadkillguy said:**
> 
Is there any reason you would be modifying the input to operator=?  I suppose I should use const more.
[/QUOTE}

Here is reason 1.

> 
```
Network.cpp:140: error: passing ‘const Network’ as ‘this’ argument of ‘int Network::getInputNum()’ discards qualifiers
```

Not sure what to do at this point.  What's wrong with calling a member function of a const class?


There is nothing wrong except that if you are simply returning the value of a property your function should be declared "const".

And that would be reason 2 to read the books I mentioned.


[QUOTE]
I've been coding c++ for just under a year... please point out to me what's wrong.

3.  Deleting the pointers and in the same token popping elements from the vector, just delete the pointers and let the system simply delete vector when the object is destroyed.

I would very seriously suggest you invest some money into these books because if you continue coding in C++ do need to read them.

---

### Post by roadkillguy on 2011-09-06
> There is nothing wrong except that if you are simply returning the value of a property your function should be declared "const".

Ahhh ok.  I think I understand const now.

> 3. Deleting the pointers and in the same token popping elements from the vector, just delete the pointers and let the system simply delete vector when the object is destroyed.

Unless clear() is a public member function for a reason.  I want to be able to clear a class without destroying it.  Operator=() does that, and I save code duplication and looping by using a clear() function.

I don't have a lot of money right now (College freshman) but I'll probably get [this]("http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=sr_1_12?s=books&ie=UTF8&qid=1315320974&sr=1-12") one.

Thanks for the help.

---

### Post by karlson on 2011-09-06
> **roadkillguy said:**
> 
Unless clear() is a public member function for a reason.  I want to be able to clear a class without destroying it.  Operator=() does that, and I save code duplication and looping by using a clear() function.


Unless you are proposing to have a destruction of the object to be a function other then the destructor clear should be private and my comment still stands:  delete memory from pointers and then call <vector>.clear() that way you are doing memory allocation only once.

> 
I don't have a lot of money right now (College freshman) but I'll probably get [this]("http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=sr_1_12?s=books&ie=UTF8&qid=1315320974&sr=1-12") one.


That's what libraries are for.

---

