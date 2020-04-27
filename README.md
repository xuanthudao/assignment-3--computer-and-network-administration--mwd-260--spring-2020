# Spring 2020 Computer and Network Administration — Assignment 3

* **Do not start this project until you have read these instructions carefully.**  
* **Read these instructions repeatedly until you understand, then begin your project. If something is not clear, ask.**  

## ❖・Introduction・❖
The answers to all the following questions should be included between the fenced backticks following each question. You may need to log in to the Linux systems on campus to test your answers. Recall that you can remotely connect to the Linux boxes using a variant of the command `ssh USER@user-COMPUTER.cs.hartford.edu`, where `USER` is the user you created at the beginning of the semester, and `COMPUTER` is one of `autechre`, `bauhaus`, `cappadonna`, `deftones`, `eluvium`, or `fugees`. For instance, if I wanted to log in to the `bauhaus` machine, I’d do so as follows:

```bash
ssh roy@user-bauhaus.cs.hartford.edu
```

## ❖・Questions・❖

### Question 1
Write a script that recursively copies all the files in one folder to another folder. The names of both folders should be arguments to the script. (_`12` pts_)

```
#!/bin/sh
folder1=./folder1
folder2=./folder2

cp -r "$folder1" "$folder2"
exit 0
```

### Question 2
Write a script that checks whether a program exists on your machine. If it doesn’t, it should try to fetch the program via `apt install`. (_`12` pts_)

```
#!/bin/sh

check_for_program() {
  local program 
  program="${1}"

  printf "Checking for ${program}\\n"
  command -v "${program}"

  if [[ "${?}" -ne 0 ]]; then
    do apt install
    done
  fi 
}
exit 0
```

### Question 3
Write a command that will create an empty file with a `.txt` extension named after the current folder. (_`12` pts_)

```
touch ..txt
```

### Question 4
Write a command that will recursively remove files with the `.thumbs` extension from the current folder. (_`12` pts_)

```
find . -name "*.thumbs" -r -type f -delete
```

### Question 5
Write a command that will recursively remove empty folders from the current folder. (_`12` pts_)

```
find . -type d -r -empty -print
```

### Question 6
Write a script that reports every file name in a folder as two items: the filename and its extension. Each item should appear on a new line. (_`12` pts_)

```
#!/bin/sh
echo '"File Name","Extension"'
for filename in `ls -lrt *.*`; do
        name=$(echo "$filename" | cut -f1 -d '.')
        extension=$(echo "$filename" | cut -d'.' -f2)
        echo '"'$size'","'$extension'"'
done
exit 0
```

### Question 7
Write a script that requests the user answer `y` or `n` to a prompt, and only exits when either of the two responses is entered. The user’s response should be echoed to the screen _before_ the program exits. (_`28` pts_)

```
#!/bin/bash

read -p "Please input 'y' or 'n': "  input
	if input != 'y' || input != 'n' || input == ""; then
	echo "Error"
	else
	echo "Your answer $input!"
fi

exit 0
```

## ❖・Due・❖
Monday, 27 April 2020, at 09:00 AM.

## ❖・Submission・❖
You will need to issue a pull request back into the original repo, the one from which your fork was created for this project. See the **Issuing Pull Requests** section of [this site](http://code-warrior.github.io/tutorials/git/github/index.html) for help on how to submit your assignment.

**Note**: This assignment may *only* be submitted via GitHub. **No other form of submission will be accepted**.
