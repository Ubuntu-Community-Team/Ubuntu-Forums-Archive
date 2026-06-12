---
title: "API MySQL problem in C"
date: 2010-12-01
forum: Programming Talk
---

### Post by zakariae_tr on 2010-12-01
[COLOR=#000000]Hello everyone, I  want to write a C program that  uses the API to communicate with a MySQL  database but I can not locate  where there is an error![/COLOR]


```


#include <stdio.h>
#include <stdlib.h>
#include <mysql/mysql.h>


int main(int argc, char*argv[])
{
    MYSQL *conn;

    MYSQL_RES *result;
    MYSQL_ROW elementsColonne;

    unsigned int nbColonnes;
    int i;
    // initialisation
    if((conn = mysql_init(NULL)) == NULL)
    {
        printf("Erreur d'initialisation\n");
        return 0;
    }

    // connexion au serveur (ici, en local)
    if(mysql_real_connect(conn,"localhost","root","zakariae","ma_base",0,NULL,0)!=0)
    {
        printf("Erreur de connexion\n");
        return 0;
    }
    printf("Connexion reussit\n");
    // on lance la requête
    if (mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`, `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")==0)
        printf("Insertion faite\n");
    else
        printf("Erreur dans l'insertion \n");

    if (mysql_query(conn,"SELECT * FROM table")==0)
    {
        printf("Erreur dans la requête\n");
        return;
    }
    else // requête bonne, traitons les données qu'elle renvoit
    {
        result = mysql_store_result(conn);
        if (result != NULL)  // MySQL peut extraire des résultats
        {
            nbColonnes = mysql_num_fields(result);

            // récupère les enregistrements un par un
            while ((elementsColonne = mysql_fetch_row(result)))
            {
                for (i = 0; i < nbColonnes; i++)
                    printf("%s\t", (elementsColonne[i] != NULL) ? elementsColonne[i] : "NULL");
                printf("\n");
            }
            // on libère la mémoire prise pour les résultats
            mysql_free_result(result);
        }
        else
            printf("Aucun résultat à la requête !\n");
    }

    // on ferme la connexion au serveur MySQL
    mysql_close(conn);
}

```

---

### Post by Arndt on 2010-12-01
> **zakariae_tr said:**
> [COLOR=#000000]Hello everyone, I  want to write a C program that  uses the API to communicate with a MySQL  database but I can not locate  where there is an error![/COLOR]


```


#include <stdio.h>
#include <stdlib.h>
#include <mysql/mysql.h>


int main(int argc, char*argv[])
{
    MYSQL *conn;

    MYSQL_RES *result;
    MYSQL_ROW elementsColonne;

    unsigned int nbColonnes;
    int i;
    // initialisation
    if((conn = mysql_init(NULL)) == NULL)
    {
        printf("Erreur d'initialisation\n");
        return 0;
    }

    // connexion au serveur (ici, en local)
    if(mysql_real_connect(conn,"localhost","root","zakariae","ma_base",0,NULL,0)!=0)
    {
        printf("Erreur de connexion\n");
        return 0;
    }
    printf("Connexion reussit\n");
    // on lance la requête
    if (mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`, `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")==0)
        printf("Insertion faite\n");
    else
        printf("Erreur dans l'insertion \n");

    if (mysql_query(conn,"SELECT * FROM table")==0)
    {
        printf("Erreur dans la requête\n");
        return;
    }
    else // requête bonne, traitons les données qu'elle renvoit
    {
        result = mysql_store_result(conn);
        if (result != NULL)  // MySQL peut extraire des résultats
        {
            nbColonnes = mysql_num_fields(result);

            // récupère les enregistrements un par un
            while ((elementsColonne = mysql_fetch_row(result)))
            {
                for (i = 0; i < nbColonnes; i++)
                    printf("%s\t", (elementsColonne[i] != NULL) ? elementsColonne[i] : "NULL");
                printf("\n");
            }
            // on libère la mémoire prise pour les résultats
            mysql_free_result(result);
        }
        else
            printf("Aucun résultat à la requête !\n");
    }

    // on ferme la connexion au serveur MySQL
    mysql_close(conn);
}

```

I think you need to point out what the error is, and where, and when it happens.

---

### Post by dwhitney67 on 2010-12-01
The following line looks suspect:
```

if (mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`, `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")==0)

```

For one, I do not think that the single-quotes are necessary in your case, and for some of those that you use (around ma_base, table, nom, prenom, login, and passe), you are using the incorrect symbol.

There's a difference between ` and '.


Btw, typically when an error occurs in a C program, one returns a non-zero value, not 0 as you have.  You need to also add a value to one of your return statements, and you should insert a return statement (w/ value) at the end of the main() function.

---

### Post by zakariae_tr on 2010-12-01
> **dwhitney67 said:**
> The following line looks suspect:
```

if (mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`, `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")==0)

```For one, I do not think that the single-quotes are necessary in your case, and for some of those that you use (around ma_base, table, nom, prenom, login, and passe), you are using the incorrect symbol.

There's a difference between ` and '.


Btw, typically when an error occurs in a C program, one returns a non-zero value, not 0 as you have.  You need to also add a value to one of your return statements, and you should insert a return statement (w/ value) at the end of the main() function.

tks  !!!
yes i agree with for the presence of ` it's not necessary ,
but the problem i have ,located in  
```
if (mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`,  `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")==0)
```

also 
```
[COLOR=Green]result = mysql_store_result(conn);
[/COLOR] 
```

---

### Post by zakariae_tr on 2010-12-01
> **dwhitney67 said:**
> The following line looks suspect:
```

if (mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`, `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")==0)

```For one, I do not think that the single-quotes are necessary in your case, and for some of those that you use (around ma_base, table, nom, prenom, login, and passe), you are using the incorrect symbol.

There's a difference between ` and '.


Btw, typically when an error occurs in a C program, one returns a non-zero value, not 0 as you have.  You need to also add a value to one of your return statements, and you should insert a return statement (w/ value) at the end of the main() function.

tks !!
 the problem that i have is located in  
```
[COLOR=Green]mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`, `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")[/COLOR]
```

also 

```
[COLOR=Green]mysql_query(conn,"SELECT * FROM table")[/COLOR]
```

---

### Post by Some Penguin on 2010-12-02
*Why* are you using so many quotes?

---

