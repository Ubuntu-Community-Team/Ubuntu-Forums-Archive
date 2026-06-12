---
title: "State machines in C++, is this any good?"
date: 2010-09-29
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-29
OK so I was snuffling through some ancient code of mine and came across my blue print for doing state machines (sample below). IDK anyone else ever program state machines? Is this idea worth pursuing?
```


#include <stdio.h>

/*
 * Base class for making state machines
 */
struct cs_state {
	typedef void (cs_state::*state)(void); // current state "method"
	state State; // current state of machine
	// run the state machine
	void operator() (void) {
		// NULL state signals the machine terminated
		if (State) (this->*State)();
	}
	bool done() { return State == (state) NULL; }        
	// constructor sets initial state	
	cs_state(state InitialState) { State = InitialState; }
	// virtual destructor so derivatives can have specialized
	// tidy up methods.
	virtual ~cs_state() {};
};

// A derived state machine just for demo-porpoises
struct test_state_machine: cs_state {
	// has two states
	void astate();
	void bstate();
	// constructor starts it in "a" state
	test_state_machine(): cs_state((state) &test_state_machine::astate) {}
	~test_state_machine() {
		printf("all done... bai!\n");
	}
};

void test_state_machine::astate() {
	printf("doing astate, press a key\n");
	getchar();
	State = (state) &test_state_machine::bstate;
}

void test_state_machine::bstate() {
	printf("doing bstate, press a key\n");
	getchar();
	State = NULL;
}

int main() {
	test_state_machine Tester;
	while (!Tester.done()) Tester(); // call state machine until it finishes
	return 0;
}

```

---

### Post by NovaAesa on 2010-09-29
I have written state machines before. I have found it easier to just have one "state machine" class, which accepts a list of states and a list of transitions, accept and reject states etc. Then for each actual state machine, you just load the state machine class with different states and transitions.

Of course, it could work the way you are doing it as well.

---

### Post by spjackson on 2010-09-30
> **worksofcraft said:**
> OK so I was snuffling through some ancient code of mine and came across my blue print for doing state machines (sample below). IDK anyone else ever program state machines? Is this idea worth pursuing?

If you have any interest in Qt, then it might be worth looking at QStateMachine [http://doc.trolltech.com/4.6/qstatemachine.html](http://doc.trolltech.com/4.6/qstatemachine.html) . Even if you decide not to use it and implement your own instead, it might give you some useful ideas.

I suppose there are other libraries out there that provide something similar, but I happen to be familiar with Qt, though I haven't actually used QStateMachine myself.

---

### Post by GeneralZod on 2010-09-30
Boost also has a state machine library, though I have not used it myself:

[http://www.boost.org/doc/libs/1_44_0/libs/statechart/doc/tutorial.html](http://www.boost.org/doc/libs/1_44_0/libs/statechart/doc/tutorial.html)

---

### Post by worksofcraft on 2010-09-30
Thanks for the suggestions I shall be looking at them both asap :)
I tried putting said idea to the test with a non-trivial and genuine application and soon found two things lacking:
[LIST=1]
[*]A system for getting getting the next 'token' or event or whatever is driving the state machine.
[*] A way to associate code with entering a state, not just with being in that state.
[/LIST]

p.s. update: The QT state machine looks very well suited to handling gui input events and the boost library also has this event handling capability. They use a state object to represent the current state of the machine. The constructor and destructor of said state object is a very handy way to associate code with entering and leaving a state :)

Currently my application centers on parsing large numbers of complicated text strings on a character by character basis so I am still a little concerned about the performance impact of making each character  into an event and also the dynamic construction and destruction of the state object on every state transition. I think I'll try implementing the same state machine with all three methods and then to work out a way of comparing performance and how easy they are to code with.

---

