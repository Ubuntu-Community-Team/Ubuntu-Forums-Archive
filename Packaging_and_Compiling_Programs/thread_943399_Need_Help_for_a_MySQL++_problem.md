---
title: "Need Help for a MySQL++ problem"
date: 2008-10-10
forum: Packaging and Compiling Programs
---

### Post by qixin1984 on 2008-10-10
Hello everyone,

I have a problem when using Mysql++ to do db operations.
Here are my codes:
//////////////////////////main function///////////////////////////////////
#include <iostream>
#include <string>

#include <mysql++.h>
using namespace std;
using namespace mysqlpp;

#include "function.h"

int main(int argc, char* argv[]){

	string Db("mysql_cpp_data");
	string User("root");
	string Password("jiajia");
	string Server("localhost");
	Connection * conn = GetNewConnection(Db,Server,User,Password);
	string queryone("select * from stock");
	string querytwo("select * from stock");

	conn->set_option(new MultiStatementsOption(true));

	SendUpdateQuery(conn,queryone);
	SendQuery(conn,querytwo);

	return 1;
}
///////////////////////////function.h/////////////////////////////////////
#include <string>

#include <mysql++.h>

using namespace std;
using namespace mysqlpp;

Connection* GetNewConnection(string & db,string & host, string & user, string & pwd);

void SendUpdateQuery(Connection * con, const string& action);

void SendQuery(Connection * con , const string& action);
/////////////////////////////function.cpp/////////////////////////////////
#define EMSG "ERROR: function.cpp:\n\t"

#include <iostream>
#include <string>
#include <cstdlib>

#include <mysql++.h>

#include "function.h"

using namespace std;
using namespace mysqlpp;


Connection * GetNewConnection(string & db,string & host, string & user, string & pwd){

    Connection* newConn = new Connection(true);
    try {
        newConn->set_option(new MultiStatementsOption(true));
        newConn->connect(db.c_str(), host.c_str(), user.c_str(), pwd.c_str(), 3306);
    } catch (exception& er) {
        cerr << EMSG << "Connection failed: " << er.what() << endl;
		exit(-1);
    }
	return newConn;
}

void SendUpdateQuery(Connection * con, const string& action) {
	
         	try {
			if (!con->connected()) {
				cerr << EMSG << "SendUpdateQuery failed: this connection is close" << endl;
				return;
			   }
			else{	
				Query query=con->query();
				query<<action.c_str();
			        query.execute();
				return;
			     } 
			}
		catch (const Exception& er) {
				cerr << EMSG << "SendUpdataQuery failed:" << er.what() << endl;
				return;
			}
}

void SendQuery(Connection * con , const string& action) {

		try {
			if (!con->connected()) {
				cerr << EMSG << "SendQuery failed: this connection is close" << endl;
				return;
			   }
			else{
				Query query1=con->query();
				query1<<action.c_str();
			        query1.execute();
				
				return;
			     } 
		}
		catch (const Exception& er) {
				cerr << EMSG << "SendQuery failed:" << er.what() << endl;
				return;
		}
}
//////////////////////////////////////////////////////////////////////////

This program compiles well. But when it runs, it throw an exception: 
"ERROR: function.cpp:
	SendQuery failed:Commands out of sync; you can't run this command now"

I don not know why... SOS!:)

---

