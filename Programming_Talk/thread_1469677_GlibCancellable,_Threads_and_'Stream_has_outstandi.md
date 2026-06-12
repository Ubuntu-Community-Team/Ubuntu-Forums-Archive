---
title: "Glib::Cancellable, Threads and 'Stream has outstanding operations' error"
date: 2010-05-02
forum: Programming Talk
---

### Post by dennis90 on 2010-05-02
Hi!

This is glibmm related.
I am writing a network application. The client sends a number to the server and the server sends it back with 2 seconds delay. (Of course this is just an example to represent the problem :) )
When the client starts, it connects to the server and sends a number. Then it starts two threads, worker() and worker2(). worker() immediately reads from the connection while worker2() waits 1 second and then cancels worker()'s read operation using a cancel object. Then worker2() also tries to read from the connection but gets the following exception: "Stream has outstanding operations."

The question is how can I get rid of it. I assumed that cancelling means that I can use my SocketConnection again.

I also tried calling clear_pending() on the SocketConnection but didn't help much...

Here is the code: 
```

#include <gtkmm.h>
#include <unistd.h>
#include <iostream>

using namespace Gtk;
using namespace Glib;
using namespace Gio;
using namespace std;

	//This is the IO stream towards the server
RefPtr<SocketConnection> c;
	//This cancellable object is used to 'steal' read from worker()
RefPtr<Cancellable> cancel;
	//This mutex protects cout
Mutex * outMut;

void worker()
{
		//worker would like to receive the number to this variable
	unsigned d=0;
	try
	{
		int k=c->get_input_stream()->read(&d,sizeof(unsigned),cancel);
		if(k<=0)
			cout << "w1: Disconnect" << endl;
	}
	catch(Gio::Error& e)	//Here an exception is caught when the read() above is cancelled
	{
		Mutex::Lock lock(*outMut);
		cout << "w1: " << e.what() << endl;
	}
	return;
};

void worker2()
{
		//worker2 would like to receive the number to this variable
	unsigned d=0;	
		//waits for a second
	sleep(1);
	cout << "Canceling...\n";
		//Cancels. Theoritically at this point an exception is thrown in the other thread
	cancel->cancel();
		//Reset the cancel object so it won't cancel the read() below immediately
	cancel->reset();
	try
	{
			//Receives the number
		int k=c->get_input_stream()->read(&d,sizeof(unsigned),cancel);
		if(k<=0)
			cout << "w2: Disconnect" << endl;
	}
	catch(Gio::Error& e)	//HERE is the point where SOMETIMES an exception occurs saying: Stream has outstanding operations
	{
		Mutex::Lock lock(*outMut);
		cout << "w2: " << e.code() << " - " << e.what() << endl;
	}
	
	{		//Print the number to stdout
		Mutex::Lock lock(*outMut);
		cout << "Read complete (w2): " << d << endl;
	}
};


int main(int argc, char ** argv)
{
		//Initialization stuff
	Gtk::Main::init_gtkmm_internals(); 
	Glib::thread_init();
	
		//Mutex for cout
	outMut=new Mutex();
	
		//Setting up socket
	RefPtr<SocketClient> sock=SocketClient::create();
	sock->set_family(SOCKET_FAMILY_IPV4);
	sock->set_protocol(SOCKET_PROTOCOL_TCP);
	sock->set_socket_type(SOCKET_TYPE_STREAM);

	try
	{
			//Connection to host
		c=sock->connect_to_host("localhost",7776);
	}
	catch(Gio::Error& e)
	{
		cout << e.what() << "\n";
		exit(1);
	}
	
		//Creating the cancellable
	cancel=Cancellable::create();

		//I send a number to the server
	unsigned d=7;
	c->get_output_stream()->write(&d,sizeof(d));
	c->get_output_stream()->flush();

		//Create the receiver threads
	Thread * t1=Thread::create(sigc::ptr_fun(&worker),true);
	Thread * t2=Thread::create(sigc::ptr_fun(&worker2),true);
	
		//Wait for them to finish
	t1->join();
	t2->join();
		//Free the mutex
	delete outMut;
	return 0;
}

```

Thank you,
Dennis

---

### Post by dennis90 on 2010-05-02
Never mind, I managed to solve it.
After calling cancel->cancel() in worker2(), it should wait for a barrier to ensure that worker() canceled properly. And worker should reach the barrier in its exception handler. That's all. :)

---

