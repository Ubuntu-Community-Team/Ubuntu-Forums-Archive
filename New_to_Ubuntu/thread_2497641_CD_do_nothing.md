---
title: "CD do nothing"
date: 2024-05-13
forum: New to Ubuntu
---

### Post by vanholder on 2024-05-13
```
maxim@I-ll-find-u:~$ pwd
/home/maxim
maxim@I-ll-find-u:~$ cd project/
maxim@I-ll-find-u:~$ pwd
/home/maxim
maxim@I-ll-find-u:~$ ^C
maxim@I-ll-find-u:~$ 



```
Trying to move to project catalog, and nothing hepend. How to fix dis issue?

---

### Post by Holger_Gehrke on 2024-05-13
What shell are you using ?
```

echo $SHELL

```
Does the directory you're trying to change to exist
```

ls project

```
Check whether you're using a restricted shell (in bash the following will tell you ...)
```

shopt|grep '^restricted'

```

Holger

---

### Post by vanholder on 2024-05-13
```
maxim@I-ll-find-u:~$ echo $SHELL
/bin/bash
maxim@I-ll-find-u:~$ ls project
test-calc
maxim@I-ll-find-u:~$ shopt|grep '^restricted'
restricted_shell    off

```

---

### Post by Holger_Gehrke on 2024-05-13
Does anybody else have access to your machine ? Some practical joker might have redefined 'cd' as an alias for ':' (a do-nothing command). Check
```

LANG=C type cd

```
This should show 'cd is a shell builtin'. If it says something about an alias or a function instead ...

Holger

---

### Post by vanholder on 2024-05-14
```

maxim@I-ll-find-u:~$ LANG=C type cd
cd is a function
cd () 
{ 
    if __gvm_is_function __gvm_oldcd; then
        __gvm_oldcd $*;
    fi;
    local dot_go_version dot_go_pkgset rslt;
    local defaults_go_name defaults_go_pkgset;
    local defaults_resolved=false;
    local defaults_hash;
    defaults_hash=();
    if [[ "$GVM_ROOT" == "" ]]; then
        display_error "GVM_ROOT not set. Please source \$GVM_ROOT/scripts/gvm";
        return $?;
    fi;
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Resolving defaults...";
    defaults_hash=($(__gvm_read_environment_file "${GVM_ROOT}/environments/default"));
    if [[ $? -eq 0 ]]; then
        defaults_resolved=true;
    else
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Can't find default environment. Falling back to system.";
        defaults_hash=($(__gvm_read_environment_file "${GVM_ROOT}/environments/system"));
        if [[ $? -eq 0 ]]; then
            defaults_resolved=true;
        else
            [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Can't find system environment.";
        fi;
    fi;
    if [[ "${defaults_resolved}" == false ]]; then
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Resolving fallback go version and pkgset from all available.";
        local fallback_go_version="$(__gvm_resolve_fallback_version)";
        local fallback_go_pkgset="$(__gvm_resolve_fallback_pkgset "${fallback_go_version}")";
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "=======================================";
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "fallback_go_version => $fallback_go_version";
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "fallback_go_pkgset => $fallback_go_pkgset";
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "=======================================";
        defaults_hash=($(setValueForKeyFakeAssocArray "gvm_go_name" "${fallback_go_version}" "${defaults_hash
[*]}"));
        defaults_hash=($(setValueForKeyFakeAssocArray "gvm_pkgset_name" "${fallback_go_pkgset}" "${defaults_hash
[*]}"));
        unset fallback_go_version;
        unset fallback_go_pkgset;
        defaults_resolved=true;
    fi;
    defaults_go_name="$(valueForKeyFakeAssocArray "gvm_go_name" "${defaults_hash
[*]}")";
    defaults_go_pkgset="$(valueForKeyFakeAssocArray "gvm_pkgset_name" "${defaults_hash
[*]}")";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++++++";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "defaults_go_name => $defaults_go_name";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "defaults_go_pkgset => $defaults_go_pkgset";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++++++";
    if [[ "${GVM_DEBUG}" -eq 1 ]]; then
        echo "Resolved default go: ${defaults_go_name:-[EMPTY]}";
        echo "Resolved default pkgset: ${defaults_go_pkgset:-[EMPTY]}";
    fi;
    dot_go_version="$(__gvmp_find_closest_dot_go_version)";
    rslt=$?;
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "---------------------------------------";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "dot_go_version => $dot_go_version";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "defaults_go_name => $defaults_go_name";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "---------------------------------------";
    if [[ $rslt -eq 0 ]]; then
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Found dot_go_version: ${dot_go_version}";
        local use_goversion="$(__gvmp_read_dot_go_version "${dot_go_version}")";
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Switching to: ${use_goversion}";
        gvm use "${use_goversion}" || return 1;
        unset use_goversion;
    else
        if [[ -n "${defaults_go_name}" ]]; then
            [[ "${GVM_DEBUG}" -eq 1 ]] && echo "No .go-version found. Using system or default go.";
        else
            if [[ "${GVM_DEBUG}" -eq 1 ]]; then
                echo "No fallback go version could be found.";
                if [[ ! -d "$GVM_ROOT/archive/go" ]]; then
                    echo "$(locale_text_for_key "go_install_prompt")";
                fi;
            fi;
            return 0;
        fi;
    fi;
    dot_go_pkgset="$(__gvmp_find_closest_dot_go_pkgset)";
    rslt=$?;
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "--------------------------------";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "dot_go_pkgset => $dot_go_pkgset";
    [[ "${GVM_DEBUG}" -eq 1 ]] && echo "--------------------------------";
    if [[ $rslt -eq 0 ]]; then
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Found .go-pkgset: ${dot_go_pkgset}";
        local use_gopkgset="$(__gvmp_read_dot_go_pkgset "${dot_go_pkgset}")";
        [[ "${GVM_DEBUG}" -eq 1 ]] && echo "Switching to: ${use_gopkgset}";
        gvm pkgset use "${use_gopkgset}" || return 1;
        unset use_gopkgset;
    else
        if [[ -n "${defaults_go_pkgset}" ]]; then
            [[ "${GVM_DEBUG}" -eq 1 ]] && echo "No .go-pkgset found. Using system or default pkgset.";
            [[ "${GVM_DEBUG}" -eq 1 ]] && echo "----------    defaults_go_pkgset => $defaults_go_pkgset     ----------";
        else
            [[ "${GVM_DEBUG}" -eq 1 ]] && echo "No fallback pkgset could be found.";
        fi;
    fi;
    return 0
}



```

---

### Post by Holger_Gehrke on 2024-05-14
Do you use the 'Go Environment Manager 2' ? A search  for '__gvm_is_function' lead me directly to [an error report]("https://github.com/markeissler/gvm2/issues/9") for gvm2 on github where somebody is having exactly the same problem you have.

Holger

---

### Post by biledk on 2024-05-14
Hey Vanholder, cant you use a different shell? Like bash, just to see if the problem persists?

---

