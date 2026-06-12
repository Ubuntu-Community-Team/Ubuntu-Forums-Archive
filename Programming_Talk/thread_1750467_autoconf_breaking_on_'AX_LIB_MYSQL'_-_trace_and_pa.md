---
title: "autoconf breaking on 'AX_LIB_MYSQL' - trace and packages installed"
date: 2011-05-05
forum: Programming Talk
---

### Post by dubayou on 2011-05-05
I need to build some software for work that requires the use of a mysql client lib.  Im pretty sure i have it install and that m4 or something isnt right.  any ideas?

```
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
./configure: line 4759: syntax error near unexpected token `AX_LIB_MYSQL'
./configure: line 4759: `AX_LIB_MYSQL()'

```

```
root@mrvoid:~# aptitude search libmysql
i   libmysql++-dev                                                         - MySQL C++ library bindings (development)
p   libmysql++-doc                                                         - MySQL C++ library bindings (documentation)
i A libmysql++3                                                            - MySQL C++ library bindings (runtime)
p   libmysql-cil-dev                                                       - MySQL database connector for CLI
p   libmysql-java                                                          - Java database (JDBC) driver for MySQL
p   libmysql-ocaml                                                         - OCaml bindings for MySql
p   libmysql-ocaml-dev                                                     - OCaml bindings for MySql
v   libmysql-ocaml-dev-u0s33                                               -
v   libmysql-ocaml-u0s33                                                   -
p   libmysql-ruby                                                          - MySQL module for Ruby
p   libmysql-ruby1.8                                                       - MySQL module for Ruby 1.8
p   libmysql-ruby1.9.1                                                     - MySQL module for Ruby 1.9.1
p   libmysql6.0-cil                                                        - MySQL database connector for CLI
p   libmysql6.1-cil                                                        - MySQL database connector for CLI
i   libmysqlclient-dev                                                     - MySQL database development files
v   libmysqlclient15-dev                                                   -
i A libmysqlclient16                                                       - MySQL database client library
pi  libmysqlclient16-dev                                                   - MySQL database development files - empty transitional package
p   libmysqlcppconn-dev                                                    - MySQL Connector for C++ (development files)
p   libmysqlcppconn4                                                       - MySQL Connector for C++ (library)
p   libmysqld-dev                                                          - MySQL embedded database development files
p   libmysqld-pic                                                          - MySQL database development files

```

---

