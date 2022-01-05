* Add the following to the file `~/.ssh/config`.
```
Host <hostname>
    User timo
    IdentityFile ~/.ssh/id_rsa
```

* You can simply ssh
```
ssh <hostname>
```

# Sync Files

* sync all files
```
rsync -av --delete --exclude-from=.gitignore --exclude=.git --progress . <hostname>:/home/timo/$(basename $(pwd))/
```

* auto sync source code
```
auto-rsync . <hostname>:/home/timo/$(basename $(pwd))/ --rsync-options='--delete --exclude-from=.gitignore --exclude=.git'
```

# SSH Tunneling

```
ssh -N -L 8000:<hostname>:8000 <hostname>
ssh -N -L 5001:<hostname>:5001 <hostname>
```