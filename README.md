
16.

echo "The Fibonacci series is : "
N=6
a=0
b=1 
for (( i=0; i<N; i++ ))
do
    echo -n "$a "
    fn=$((a + b))
    a=$b
    b=$fn
done

17.

for a in 1 2 3 4 5 6 7 8 9 10
do
    # if a = 5 then continue the loop and
    # don't move to line 8
    if [ $a == 5 ]
    then
        continue
    fi
    echo "Iteration no $a"
done


11.

#! bin/bash
echo "The Fibonacci series is : "
read N a b
for (( i=0; i<N; i++ ))
do
    echo -n "$a "
    fn=$((a + b))
    a=$b
    b=$fn
done
exit 0


21.


#!/bin/bash

hour=`date +%c | tr -s " " | cut -d " " -f4 | cut -d ":" -f1`   
day=`date +%A`  
mon=`date +%B`  
dte=`date +%d`  
year=`date +%Y`  
tf=`date +%r`    
if [ $hour -ge 5 -a $hour -lt 12 ]  
then
        echo -e "Good morning `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 12 -a $hour -le 13 ]   
then
        echo -e "Good noon `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 14 -a $hour -lt 17 ]  
then
        echo -e "Good afternoon `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 17 -a $hour -lt 21 ]   
then
        echo -e "Good evening `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
elif [ $hour -ge 21 -o $hour -lt 5 ]   
then
        echo -e "Good night `whoami`, Have nice day!\nThis is $day $dte in $mon of $year ($tf)"
fi

11.
#!/bin/bash


echo "Enter the value of n:10"
read Num

f1=0
f2=1

echo "The Fibonacci Nos <= $Num is : "

i=0
while [ $f1 -le $Num ]
do
    echo -n "$f1 "
    fn=$((f1+f2))
    f1=$f2
    f2=$fn
done
echo
 
10.

#!/bin/bash
echo "give me a number or string"
read a
i=$((${#a}-1))
echo ${a:$i:1}

13.

#!/bin/bash
echo "Chess Board"

for (( i=1; i<=8; i++))
do
        for (( j=1; j<=8; j++))
        do
                total=$(($i+$j))
                temp=$(($total%2))
                # for alternative blocks
                if [ $temp -eq 0 ]
                then
                        echo -e -n "\033[47m" " "  #white
                else
                        echo -e -n "\033[40m" " " #black
                fi
        done
        echo -e -n "\033[0m" " "
        echo ' '
done


15.

#!/bin/bash
<<COMMENT
Print Informations:
1. Currently logged user
2. Your shell directory
3. Home directory
4. OS name and version
5. Current working directory
6. Number of users logged in
7. Show all available shells in your system
8. Hard disk information
9. CPU information
10. Memory information
11. file system information
12. Currently running process
COMMENT

echo "Enter the option from 1-13 to get the particular information:
1. Currently logged user
2. Your shell directory
3. Home directory
4. OS name and version
5. Current working directory
6. Number of users logged in
7. Show all available shells in your system
8. Hard disk information
9. CPU information
10. Memory information
11. file system information
12. Currently running process"

echo -n "Choice: " ; read option

case $option in
	1) # prints the names of the users currently logged in to the current host without showing any information about source, login time, or any other relevant information 
	   echo "Currently logged user:"; users;
	   ;;
	2) #gives shell name relative to root
	   echo "Your shell directory: $SHELL"
	   ;;
	3) echo "Home directory: $HOME"
	   ;;
	4) echo -n "operating system name is:  "; uname -s ; #uname
  	   echo -n "operating system version is:  "; uname -v
	   echo -n "operating system release is:  "; uname -r
        #echo -n network hostname: ; uname -n
	   #echo -n hardware name: ; uname -m
     	   ;; 
	5) echo "Current working directory: $PWD"
   	   ;;
	6) echo -n "Number of users logged in is: "
   	   who -u | wc -l
	   #who -q
	   ;;
	7) cat /etc/shells | grep -v "#"
	   ;;
	8) echo "Hard disk information:"
        diskutil list #in MAC
        #for further detailed information of each physical disk
        diskutil info disk0
        diskutil info disk1

        #sudo lshw -short
	    #sudo hdparm -I /dev/sda
	   ;; 
	9) echo "CPU information:"
        #in MAC
        echo "Chip Brand – Processor Type and Chip Model – CPU Speed"
        sysctl -n machdep.cpu.brand_string

        #CPU details
        sysctl -a | grep machdep.cpu
        #CPU Processor Details of a Mac with system_profiler
        #system_profiler

        #sudo lscpu
	   #cat /proc/cpuinfo
	   ;;
	10)echo "Memory information:"
        #in MAC
        sysctl -a | grep mem

        #cat /proc/meminfo
	   ;;
	11)echo "file system information:"
	   df -H
	   #fdisk -1 ; mount
	   ;;
	12)echo "Currently running process:"
	   ps
 	   #gives currently running process dynamically
	   #top 
	   ;; 
	*)echo "Invalid option:"
	   ;;
esac


14.

#!/bin/bash
echo "give 5 number and orderd or underderd array"
read a b c d e f g

arr=($a $b $c $d $e)

echo "Array in original order"
echo ${arr[*]}

for ((i = 0; i<5; i++))
do

    for((j = 0; j<5-i-1; j++))
    do

        if [ ${arr[j]} -gt ${arr[$((j+1))]} ]
        then
            # swap
            temp=${arr[j]}
            arr[$j]=${arr[$((j+1))]}
            arr[$((j+1))]=$temp
        fi
    done
done

echo "Array in sorted order :"
echo ${arr[*]}

echo "Array in sorted order :"
echo ${arr[*]} | rev

24.     (First need to create directory mkdir {dir.name}
Next Create 5 swap file command = touch .{1..5}.swp
Next ls -la check swap files 
goto that directory cd{dir.name}
create file assignment24.sh and paste script and excute it.
This for 24th)

if [ $# -eq 1 ]  
then
	if [ -d $1 ]  
	then
		swps=(`find $1 -name "*.swp" -type f`)  
		if [ ${#swps[@]} -ne 0 ]  
		then
			find $1 -name "*.swp" -type f -delete   
		else
			echo "No swp files found in test_swp."
		fi
	else
		echo "Error : '$1' no such a file or directory"
	fi
else
	swps=(`find ~ -name "*.swp" -type f`)  
	if [ ${#swps[@]} -ne 0 ]  
	then
		echo "swap file found :"
		find ~ -name "*.swp" -type f  
	fi
fi

19.

for i in {1..10}  
do  
touch $i.txt;  
done;  


for i in *.txt  
do  
echo $i;  
done;  

for i in *.txt  
do  
newfile=${i/.txt/.zip};  
echo $newfile;  
done;  

for i in *.txt  
do  
newfile=${i/.txt/.zip};  
mv $i $newfile;  
done:  
ls -lta


33.

#!/bin/bash

arr=(`printenv PATH | tr ":" " "`)  
total=0  
for i in ${arr[@]}   
do
	if [ -d $i ]  
	then
		cd $i   
		count=0  
		for j in `ls`  
		do
			if [ -f $j -a -x $j ]  #
			then
				let count=$count+1   
			fi
		done
		echo -e "Current dir: $i\nCurrent count: $count"  
		let total=$total+$count   
	fi
done
echo "Total - $total"

34.  ____awk -F: '{print $1}' /etc/passwd_____

22.

#!/bin/sh
# shebang to specify that this is an shell script

# Function to get File
getFile(){
    # Reading txtFileName to convert it's content
    echo -n "Enter File Name:"
    read txtFileName
    # Checking if file exist
    if [ ! -f $txtFileName ]; then
        echo "File Name $txtFileName does not exists."
        exit 1
    fi
}

clear
  echo "1. Uppercase to Lowercase "
  echo "2. Lowercase to Uppercase"
  echo "3. Exit"
  echo -n "Enter your Choice(1-3):"
  read Ch

  case "$Ch" in
    1) 
      # Function Call to get File 
      getFile    
      # Converting to lower case if user chose 1     
      echo "Converting Upper-case to Lower-Case "
      tr '[A-Z]' '[a-z]' <$txtFileName
    ;;

    2)
      # Function Call to get File 
      getFile
      # Converting to upper case if user chose 2
      echo "Converting Lower-Case to Upper-Case "
      tr '[a-z]' '[A-Z]' <$txtFileName
    ;;
    

    *) # exiting for all other cases
        echo "Exiting..."
        exit
    ;;
  esac

32. 

#!/bin/bash


usrid=(`cut -d ":" -f3 /etc/passwd`)  
if [ $# -gt 0 ]  
then
if [ $# -eq 1 ] 
then
echo "Error : Please pass 2 arguments through CL.
Usage : ./30_user_ids.sh 100 200"
elif [ $1 -gt $2 ]    
then
echo "Error : Invalid range. Please enter the valid range through CL."
else
count=0  
for i in ${usrid[@]}  
	do
if [ $i -ge $1 -a $i -le $2 ]   
	then
  let count=$count+1
	fi
	done
	echo "Total count of user ID between $1 to $2 is : $count"
	fi
     else  
   count=0
  for i in ${usrid[@]}
	do
if [ $i -ge 500 -a $i -le 10000 ]
	then
	let count=$count+1
	fi
	done
	echo "Total count of user ID between 500 to 10000 is: $count"
         fi

31.

#!/bin/bash

filesys=(`df | tr -s " " | cut -d " " -f1`)
for j in ${filesys[@]}
do
        echo "$j"
done
useper=(`df | tr -s " " | cut -d " " -f5 | cut -d "%" -f1`)
for i in `seq $((${#useper[@]}-1))`
do
        if [ ${useper[i]} -ge 90 ]
        then
echo "Filesystem ${filesys[i]} have less than 10% free space"
fi
done

19.  

#!/bin/bash
echo "Enter the target directory "
read target_dir
cd $target_dir
 
echo "Enter the file extension to search without a dot"
read old_ext
 
echo "Enter the new file extension to rename to without a dot"
read new_ext
 
echo "$target_dir, $old_ext, $new_ext"
 
for file in *.$old_ext
do
    mv -v "$file" "${file%.$old_ext}.$new_ext"
done;

********************--------------------------------------------------***************************************************
4.

echo "what command do u want to execute-SCP or SSH"
while :
do
read INPUT_STRING
case $INPUT_STRING in
        SCP)
                echo "u have selected SCP"



               echo "please provide the username and IP"
                read a b
                scp -r $a@$b /home/$a
                ;;
        SSH)
                echo "U have selected SSH"
                echo "please provide the username and IP number of client"
                read c d
                ssh $c@$d whoami
                ;;



       *)
                echo "Not a valid argument"
                echo
esac



18

#!/bin/bash
echo "which directory you want to newname"
read a
echo "what is the new name want to give  "
read b
mv $a $b



20

#!/bin/bash
echo "what is the file to be displayed"
read a
echo "what is the starting line"
read b
echo " what is the ending line"
read c
sed -n $b,$c"p" $a


25

#!/bin/bash

 rand -c 5 -s 1 -n 3


26

#!/bin/bash
echo *



27

#!/bin/bash
 echo "please give the name of the log file to be fallowed"
read a
tail -f $a



28


#!/bin/bash

getopts a:b:c:
echo "$1"



29

#!/bin/bash
echo "give the name of the filesystem"
read a
echo "checking if the file system is mounted or not"
findmnt $a
echo "free space in the mounted filesystem"
findmnt --df



30


#!/bin/bash


echo "please provide the directory name"
read a
chmod -R 700 $a
