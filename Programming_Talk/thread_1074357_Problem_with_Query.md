---
title: "Problem with Query"
date: 2009-02-19
forum: Programming Talk
---

### Post by gvanto on 2009-02-19
I am following the first example on here: [http://tangentsoft.net/mysql++/doc/html/userman/tutorial.html]("http://tangentsoft.net/mysql++/doc/html/userman/tutorial.html")
on using the MySQL++ feature (which seems pretty powerful, i like its ability to access fields within result sets associatively)

My program has the header files included and the mysqlpp namespace is recongized, however when trying to create a query, the avaiable method in connection, takes void as argument ??

So I cant create a query right now, very frustrating :-(

I installed the following 2 packages on Kubuntu (Hardy):
> 
i   libmysql++-dev                                                            - mysql C++ library bindings (development)
i   libmysql++2c2a                                                            - mysql C++ library bindings (runtime)

Help would be greatly appreciated,
gvanto
mySQL++ newbie

> 
/*
 * testmain.cpp
 *
 *  Created on: 15/02/2009
 *      Author: pacific
 */

#include <iostream>
#include <cstdlib>
#include <stdio.h>
#include <string>
#include <stdlib.h>

#include "mysql++/mysql++.h"
#include "mysql++/query.h"
#include <mysql.h>

#define DO_MAIN 1
using namespace std;


#ifdef DO_MAIN
int main(int argc, char *argv[]) {

	mysqlpp::Connection conn(false);
	mysqlpp::Query query = conn.query("select * from stock"); //query(void) is the only available method here ! ? !



	return 0;
}

#endif



---

### Post by WW on 2009-02-19
> **gvanto said:**
> 
My program has the header files included and the mysqlpp namespace is recongized, however when trying to create a query, the avaiable method in connection, takes void as argument ??

I've never used MySQL++, so I probably can't help you myself, but it would help others to help you if you showed the exact commands that you used to try to compile this program, and show the exact error message(s) that you get.

---

### Post by gvanto on 2009-02-19
Yeah sorry I'm having total nightmares, please see my other thread for the error (which I think is related).

g

---

