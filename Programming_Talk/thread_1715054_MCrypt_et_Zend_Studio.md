---
title: "MCrypt et Zend Studio"
date: 2011-03-26
forum: Programming Talk
---

### Post by Predator44 on 2011-03-26
Bonjour,

J'ai actuellement un problème avec Zend Studio et l'extension Php MCrypt.

L'extension fonctionne correctement lorsque je lance la page via Apache mais lorsque j'essai de debugguer via Zend Studio, j'ai les erreurs suivantes : 

 Use of undefined constant MCRYPT_RIJNDAEL_256 - assumed 'MCRYPT_RIJNDAEL_256'
Debug Error:  - Call to undefined function mcrypt_module_get_algo_key_size()

J'ai essayé de configurer Zend pour utiliser php en CLI ou CGI mais cela n'a rien changer.

Quand je lance php (CLI ou CGI) en ligne de commande, je vois bien que l'extension MCrypt est installée et activée (phpinfo())

Merci pour votre aide

(Apache2, PHP5.3.2)

---

