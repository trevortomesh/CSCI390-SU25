1. # 📘 Operating Systems: A Living Textbook

   Welcome to **Operating Systems: A Living Textbook**—a continuously evolving, lecture-driven companion to your course. Every chapter is based on actual classroom instruction, cleaned up and clarified for clarity, accuracy, and real-world relevance.

   This resource is designed to help you:
   - Review lecture content in a structured way
   - See the connections between theory and practice
   - Understand core OS concepts through examples and diagrams
   - Catch up if you miss class or need reinforcement

   Each section mirrors lecture flow, from the basics of system architecture and C programming to memory management, processes, and system calls. Code examples and diagrams are integrated where helpful.

   Let’s dive in.

   
   This page is more-or-less transcribed from the lecture notes + ChatGPT.
   <u>If you spot an error (and there are many) please send a pull request!</u>

   

   ---

   ## 📑 Table of Contents

   ## Table of Contents
   
   - [Chapter 1: Introduction and Syllabus](#chapter-1-introduction-and-syllabus)
   - [Chapter 2: Operating Systems (Three Easy Pieces)](#chapter-2-operating-systems-three-easy-pieces)
   - [Chapter 3: Intro to Docker and Ubuntu](#chapter-3-intro-to-docker-and-ubuntu)
   - [Chapter 4: Intro to Linux, the Shell, and Parsers](#chapter-4-intro-to-linux-the-shell-and-parsers)
   - [Chapter 5: A Crash Course in C](#chapter-5-a-crash-course-in-c)
   - [Chapter 6: An Intro to Pointers](#chapter-6-an-intro-to-pointers)
   - [Chapter 7: malloc and free](#chapter-7-malloc-and-free)
   - [Chapter 8: Stack vs Heap (Part 2)](#chapter-8-stack-vs-heap-part-2)
   - [Chapter 9: Heap vs Stack (Part 3)](#chapter-9-heap-vs-stack-part-3)
   - [Chapter 10: Stack Growth and Lifetime](#chapter-10-stack-growth-and-lifetime)
   - [Chapter 11: The Compile-Link Cycle](#chapter-11-the-compile-link-cycle)
   - [Chapter 12: Intro to x86 Assembly](#chapter-12-intro-to-x86-assembly)
   - [Chapter 13: Intro to ARM64 Assembly](#chapter-13-intro-to-arm64-assembly)
   - [Chapter 14: Stack Frames](#chapter-14-stack-frames)
   - [Chapter 15: Instruction Flow and Control Logic](#chapter-15-instruction-flow-and-control-logic)
   - [Chapter 16: Intro to Processes](#chapter-16-intro-to-processes)
   - [Chapter 17: Context Switching, System Calls, and the User–Kernel Divide](#chapter-17-context-switching-system-calls-and-the-userkernel-divide)
   - [Chapter 18: Hardware, the Kernel, and User Processes](#chapter-18-hardware-the-kernel-and-user-processes)
   - [Chapter 19: Fork()](#chapter-19-fork)
   - [Chapter 20: Corruption Risks During Context Switches](#chapter-20-corruption-risks-during-context-switches)
   - [Chapter 21: Threads vs Processes](#chapter-21-threads-vs-processes)
   - [Chapter 22: Go, Goroutines, and Race Conditions](#chapter-22-go-goroutines-and-race-conditions)
   - [Chapter 23: Visualizing Thread Execution with Python and htop](#chapter-23-visualizing-thread-execution-with-python-and-htop)
---

More chapters will be added over time, reflecting new material, refinements, and your feedback.

Let’s get to it.


# 📘 Chapter 1: Welcome to Operating Systems & Blockchains

**Instructor**: Dr. Trevor Tomesh  
**Course**: CSCI 390 – Operating Systems and Blockchains  
**Session**: May 14 – June 27, 2025  
**Delivery**: Asynchronous, Canvas + Panopto

---

## 🧑‍🏫 About Your Instructor

Dr. Trevor Tomesh—aka “Dr. T”—teaches full-time in Wisconsin and serves as an adjunct at Ave Maria University. With roots in small-town Wisconsin and a PhD from the University of Regina in Saskatchewan, Dr. T blends academic rigor with a relaxed, approachable style. His teaching philosophy is grounded in:

- Live coding over slides
- Flexibility in pacing and assignments
- Emphasis on understanding, not memorization
- Integration of faith, reason, and technology

---

## 🎓 Course Overview

This course introduces the theory and practice behind **operating system design** and modern **blockchain systems**. It focuses on:

- Process and thread management
- Scheduling and synchronization
- Memory management and virtual memory
- System-level programming in C
- Blockchain fundamentals and consensus models

---

## 📚 Materials & Tools

- **No required textbook** to purchase  
  We'll use the open-source book:  
  [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)

- **Required Tools**:
    - Internet-connected computer
    - Docker-based Ubuntu environment (tutorial provided)
    - C programming tools (included in Docker)
    - Access to Canvas for assignments, quizzes, and lectures

---

## 🎯 Learning Outcomes

By the end of the course, you will be able to:

- Understand key OS concepts: memory, processes, synchronization
- Write C programs that demonstrate concurrency and low-level control
- Safely experiment in a containerized OS environment
- Understand blockchain structure, including cryptography and consensus

---

## 📊 Grading Breakdown

| Component                | Weight |
|--------------------------|--------|
| Projects (3 total)       | 45%    |
| Weekly Quizzes           | 15%    |
| Weekly Discussion Posts  | 5%     |
| Midterm Exam             | 15%    |
| Final Exam               | 20%    |

**Late Policy**:  
5% per day, up to a 40% deduction. Communicate with Dr. T early to arrange extensions if needed.

---

## 🤖 AI Use Policy

You *may* use ChatGPT or other LLMs with the following conditions:

- ❌ Not allowed on quizzes or exams
- ✅ Permitted on assignments with proper citation
- Cite clearly: e.g., "Some ideas in this explanation were refined with the help of ChatGPT."
- Assignments fully generated by LLMs will receive a 0, even if cited.

📖 For full details: [ChatGPT in Academia Guide](https://github.com/trevortomesh/llm-policy)

---

## 🗓️ Weekly Expectations

Each week, you’ll:

- Watch posted lecture videos
- Complete one discussion board post
- Take one quiz
- Submit any assignments due
- Practice via ungraded interactive activities

---

## 💬 A Final Word

This class is designed to challenge you—but not overwhelm you. Expect flexibility, support, and clarity throughout the course. Check Canvas often for schedule updates.

> “The goal isn’t just to write code—it’s to think deeply about how systems work.”

---

_This living textbook is co-authored by Dr. Trevor Tomesh and ChatGPT, with AI used to support clarity, structure, and instructional design._

Based on your Lecture 2 transcript, here’s Chapter 2 of the living textbook. It presents foundational concepts clearly and is designed to be copy-paste ready for your textbook.md GitHub file.

⸻


## Chapter 2: What *Is* an Operating System?

Operating systems are so integral to computing that we often refer to entire machines by the OS they run: a "Linux box," a "Windows machine," or "my Mac." But what actually *is* an operating system?

---

### 🧾 Working Definition

> **An operating system is an interface between the user and the hardware.**

This interface isn't a single program—it's a **collection of programs** that mediate access to resources, manage complexity, and prevent disaster. You can think of the OS as a multi-layered shield that:

- Manages memory, storage, and I/O
- Allows multiple programs to run concurrently
- Controls access to physical devices
- Provides safety and consistency across processes

---

### 🧱 OS Layer Diagram

User
↓
Application Layer (Programs like Chrome, VS Code, etc.)
↓
Operating System (Kernel, system calls, device drivers)
↓
Hardware (CPU, memory, storage, peripherals)

Each command from the user flows through these layers. The OS checks if the action is allowed, queues it, translates it into hardware instructions, and mediates any responses.

---

### 🧠 Why Have an OS?

A good operating system:
- Prevents the user from accidentally (or maliciously) breaking the system
- Ensures multiple processes share hardware safely
- Provides predictable interfaces for applications (APIs)
- Abstracts complex hardware into usable virtual resources

We'll focus on **Linux**, specifically **Ubuntu** via **Docker** containers, for all examples.

---

## 🧩 The Three Easy Pieces

The course textbook, *Operating Systems: Three Easy Pieces*, breaks down OS concepts into three fundamental areas:

### 1. Virtualization

> **"Turning physical hardware into easy-to-use virtual resources."**

- **Process Virtualization**: Each process thinks it owns the whole CPU and memory.
- **Machine Virtualization**: Entire virtual machines (VMs) that can run OSes.
- **Containerization**: Lightweight virtualization at the OS level. (Example: Docker)

🧪 **We’ll be using Docker to sandbox Ubuntu, avoiding damage to your actual OS while learning low-level system behaviors.**

---

### 2. Concurrency

> **"Making it seem like multiple programs run at the same time."**

- Uses threads, processes, and scheduling to simulate multitasking.
- Core components: threads, locks, semaphores, and monitors.
- Key challenges: race conditions, deadlocks, and starvation.

🧠 Example: A web server handling multiple requests simultaneously via threads.

---

### 3. Persistence

> **"Ensuring data lasts even after the power is off."**

- Involves file systems (ext4, FAT, NTFS) and block storage.
- Ensures integrity, access control, and recoverability.
- Concepts like journaling protect against crashes.

🗂️ Example: Saving a file and retrieving it after reboot.

---

## 🧮 Summary

Together, these three “easy pieces” form the core of any modern OS:

| Concept       | Purpose                                      |
|---------------|----------------------------------------------|
| Virtualization| Abstracts and multiplexes physical resources |
| Concurrency   | Enables multitasking and responsiveness      |
| Persistence   | Guarantees data longevity                    |

Mastering these will give you the tools to reason about *any* modern OS—from your smartphone to a datacenter hypervisor.

---

_Next up: diving into Ubuntu, the shell, and your Docker-based dev environment._


⸻
Here is Chapter 3 for your Operating Systems Living Textbook, based on your lecture on Docker and Ubuntu basics.

⸻


## Chapter 3: Getting Started with Docker and Ubuntu

Docker is a cornerstone of our development environment in this course. Rather than installing and risking damage to your main operating system, we’ll use Docker containers to work within a clean, isolated Ubuntu environment.

---

### 🐳 What Is Docker?

Docker is a platform that packages applications and their dependencies into **containers**. These containers behave like lightweight virtual machines:

- They **run consistently** across machines and setups
- They are **isolated** (no system-level conflicts)
- They are **lightweight** and fast to spin up
- They can be **version controlled** using Dockerfiles
- They ensure a shared and reproducible environment for all students

Think of Docker as a shipping container—no matter what’s inside, it fits and functions the same on any ship (or system).

---

### 📦 Key Concepts

| Concept        | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Image**      | A blueprint for a container, including OS, libraries, and app code         |
| **Container**  | A running instance of an image                                              |
| **Dockerfile** | A script used to build images (a "recipe")                                  |
| **Docker Hub** | A public repository for common base images like `ubuntu`, `python`, etc.   |

---

### ⚙️ Installing Docker

Follow the [Docker install tutorial on Canvas](#) for your platform (Windows, Mac, Linux). After installation:

```bash
docker --version
````
You should see the installed Docker version. Next:
```bash
docker run hello-world
```
If it prints a success message, Docker is working!

⸻

🧪 Running Ubuntu in Docker

To launch an interactive Ubuntu container:
```bash
docker run -it ubuntu
```
	•	-i means interactive
	•	-t allocates a terminal
	•	ubuntu is the name of the base image

Once inside, you’re using a bash shell in a clean Ubuntu instance.

⸻

🖥️ Useful Ubuntu Shell Commands

Command	Purpose
pwd	Show present working directory
ls	List files in the current directory
cd [dir]	Change directory
mkdir [name]	Make a new directory
touch [file]	Create a new empty file
rm [file]	Remove a file
rm -r [dir]	Recursively remove a directory
apt-get update	Update package lists
apt install micro	Install the Micro text editor


⸻

📝 Text Editors in Ubuntu

This course uses the Micro text editor for simplicity:
```bash
apt-get update
apt install micro
micro test.txt
````

Use:
	•	Ctrl + S to save
	•	Ctrl + Q to exit

⸻

🧼 Cleaning Up Docker

Command	Description
docker ps	List running containers
docker ps -a	List all containers
docker images	Show downloaded images
docker stop [container]	Stop a running container
docker rm [container]	Remove a container
docker rmi [image_id]	Remove an image


⸻

🧠 A Note on Persistence

By default, Docker containers do not persist data across runs.
That means if you install Micro and then exit the container, it will be gone next time you run it.

We’ll address how to persist changes in a later lecture.

⸻

🔚 Wrap-Up

Docker enables us to safely explore low-level system behavior in an Ubuntu sandbox. You’ll use it every day in this course. Be sure to:
	•	Successfully install Docker
	•	Run your first Ubuntu container
	•	Practice basic file and directory manipulation in the shell

⸻

Next up: digging deeper into the Linux shell, the file system hierarchy, and writing your first C programs in Docker.

---

Here is Chapter 4 of your Operating Systems Living Textbook, based on your lecture on Linux, the shell, and parsers.

⸻


## Chapter 4: Inside Linux – The Shell, the Kernel, and Parsing Commands

Before diving deeper into systems programming, we need to understand the layers that make Linux work—and how we interact with them using the shell.

---

### 🐧 What Is Linux?

Linux is an open-source operating system, inspired by Unix and developed collaboratively since 1991. Its popularity in academic, server, and development environments is due to its transparency, flexibility, and UNIX compatibility.

#### Quick History

- Created by **Linus Torvalds** in 1991 as a hobby project
- Based on **MINIX**, a lightweight Unix-like OS
- Rapidly adopted and expanded through global open-source collaboration

---

### 🧱 The Linux Architecture

The Linux OS can be understood as a layered system:

[User]
↓
[System Utilities]
↓
[System Libraries]
↓
[Kernel]
↓
[Hardware]

#### 1. **Hardware Layer**
Includes the CPU, RAM, disks, and I/O devices.

#### 2. **Kernel**
The core of the OS. It:
- Manages memory, processes, devices
- Provides abstraction over raw hardware
- Is modular, with drivers and services interacting closely with the machine

#### 3. **System Libraries**
These expose interfaces to interact with the kernel safely, including standard system calls (e.g., `open`, `read`, `write`).

#### 4. **System Utilities**
Programs like compilers, editors, and CLI tools (`ls`, `cd`, `mkdir`) used by both users and system scripts.

---

### 🐚 The Linux Shell

The **shell** is the user’s gateway into Linux. It interprets commands and executes programs on behalf of the user.

You’ve been using **Bash** (Bourne Again Shell), a common and powerful command interpreter.

#### How It Works:
1. **User inputs command**
2. **Shell parses the command**
3. **Shell forwards request to kernel**
4. **Kernel interacts with hardware and returns result**

The shell is considered the **outermost layer** of the operating system—the part the user directly touches.

---

### 🔁 The REPL Cycle

The shell operates on a REPL loop:

- **Read**: Accept input from the user
- **Evaluate**: Interpret the command or script
- **Print**: Display the result or output
- **Loop**: Wait for the next input

Example:
```bash
ls -l

	•	ls = command token
	•	-l = option token

These tokens are parsed, evaluated, and the result is printed.
```
⸻

🧠 What Is Parsing?

When you type a command like mkdir test, the shell performs lexical analysis:
	•	Breaks the string into tokens (meaningful units)
	•	Identifies keywords, variables, operators, etc.
	•	Classifies them into categories like identifiers, operators, literals

Example:

x = a + b * 2;

Lexical analysis transforms it into:

[Identifier: x], [Operator: =], [Identifier: a],
[Operator: +], [Identifier: b], [Operator: *],
[Literal: 2], [Separator: ;]

This tokenization step is part of what every shell and compiler must do to understand your input.

⸻

🧰 Key Takeaways
	•	Linux is modular and layered: hardware, kernel, libraries, utilities
	•	The shell interprets and relays user instructions to the kernel
	•	Shells use REPL and parsers to process commands
	•	Understanding parsing gives insight into how compilers and interpreters work

⸻

Up next: an introduction to C programming inside our Ubuntu environment—and a first look at pointers.

---

Here is Chapter 5: A Crash Course in C, based on your lecture transcript.

⸻


## Chapter 5: A Crash Course in C

C is a foundational programming language for systems-level work. It's fast, minimal, and dangerously powerful. In this chapter, you'll get a crash course in writing, compiling, and running C programs inside your Docker-based Ubuntu environment.

---

### ⚙️ Why C?

C is close to the hardware. It gives you direct control over:

- **Memory** (with `malloc`, `free`)
- **Pointers** and addresses
- **System calls**
- **Performance-critical code**

This power comes at a price: C doesn’t protect you from mistakes. There’s no garbage collection, and almost everything is manual.

---

### 🖥️ Your First C Program

Let’s start with the classic:

```c
#include <stdio.h>

int main() {
    printf("Hello, world!\n");
    return 0;
}
```
Save this in a file called hello.c.

To compile it:

gcc hello.c -o hello

Then run:

./hello

If all went well, you’ll see:

Hello, world!


⸻

🧠 Key C Concepts

1. Compilation
	•	C is compiled, not interpreted.
	•	You’ll use gcc to convert .c files into executable binaries.

2. Includes and Headers
	•	#include <stdio.h> brings in the standard input/output library.
	•	Header files declare functions and macros your code will use.

3. Main Function
	•	Every C program must have a main() function.
	•	return 0; tells the OS that the program ended successfully.

⸻

📦 Variables and Types

C is statically typed. You must declare the type of every variable:

int x = 5;
float y = 3.14;
char c = 'A';

Common types:
	•	int, float, double, char
	•	Arrays: int nums[5];
	•	Strings: char name[] = "Trevor";

⸻

➕ Operators

C supports familiar arithmetic:

int sum = 5 + 3;   // 8
int diff = 5 - 3;  // 2
int prod = 5 * 3;  // 15
int quot = 5 / 3;  // 1 (integer division!)


⸻

🔁 Control Structures

C includes if, else, for, while, and switch:

for (int i = 0; i < 5; i++) {
    printf("%d\n", i);
}


⸻

📂 Files, Compilation, and Debugging

Use this workflow:
	1.	Edit file: micro myprogram.c
	2.	Compile: gcc myprogram.c -o myprogram
	3.	Run: ./myprogram
	4.	If there are errors, re-edit and fix

💡 Use gcc -Wall to enable all warnings, which help catch bugs.

⸻

💥 Common Mistakes
	•	Forgetting a semicolon ;
	•	Mismatched brackets {} or parentheses ()
	•	Using undeclared variables
	•	Forgetting to #include required headers
	•	Integer division surprises

⸻

🛠️ Practice Activity

Try this in Docker:

#include <stdio.h>

int main() {
    int age;
    printf("Enter your age: ");
    scanf("%d", &age);
    printf("You are %d years old!\n", age);
    return 0;
}

Compile and run it. Try invalid inputs. Observe how it behaves.

⸻

🧠 Summary
	•	C is the language of operating systems
	•	Mastery of C is essential for kernel, memory, and performance work
	•	Compilation, pointers, memory, and manual control define C’s power and danger

⸻

Here is Chapter 6: An Introduction to Pointers, based on your lecture transcript.

⸻


## Chapter 6: An Introduction to Pointers

Pointers are often cited as the most intimidating concept in C—but they're also the most essential, especially in the world of operating systems. This chapter demystifies what pointers are, how they relate to memory, and why they matter in systems programming.

---

### 🧠 What Is a Pointer?

A **pointer** is a variable that stores the **memory address** of another variable.

Think of it as a sticky note that says, “The thing you’re looking for is in drawer 5100.” The note isn’t the thing itself—it just tells you where to find it.

```c
int x = 42;
int *p = &x;

	•	x holds the value 42
	•	&x is the address of x
	•	p holds that address
	•	*p accesses the value at that address (42)
```
⸻

🧱 Why Are Pointers Important in Operating Systems?

Pointers are foundational for:
	•	Memory management: Functions like malloc and free return and manipulate memory addresses.
	•	Data structures: Linked lists, page tables, trees—these are built with pointers.
	•	Process control: OS schedulers use linked lists of process control blocks (PCBs), linked by pointers.
	•	Hardware interaction: Memory-mapped I/O devices are accessed via direct pointer manipulation.
	•	Efficiency: Pointer arithmetic allows fast and low-level manipulation of data with minimal overhead.

Without pointers, an operating system couldn’t efficiently track processes, allocate memory, or communicate with hardware.

⸻

🔌 RAM and Addressable Memory

RAM (Random Access Memory) is made up of addressable memory cells—think of them like mailboxes, each with a unique number (address).

Declaring a variable like int a; sets aside a chunk of those mailboxes to store that value. A pointer like int *ptr; stores the address of one of those chunks.

int a = 5;
int *ptr = &a;

In memory, it might look like this:
	•	a is stored at address 0x5100 with value 5
	•	ptr is stored elsewhere, and it holds the value 0x5100

⸻

🔎 Pointer Syntax Breakdown

int y = 10;
int *ptr = &y;
*ptr = *ptr + 5;

	•	y is initialized to 10
	•	ptr stores the address of y
	•	*ptr = *ptr + 5 adds 5 to the value at that address

After this:
	•	y == 15
	•	*ptr == 15

⸻

🧪 Example: Full Code

#include <stdio.h>

int main() {
    int x = 42;
    int *p = &x;

    printf("Address of x: %p\n", (void*)&x);
    printf("Address stored in p: %p\n", (void*)p);
    printf("Value at address p: %d\n", *p);
    
    int y = 10;
    int *ptr = &y;
    *ptr = *ptr + 5;
    
    printf("y = %d\n", y);
    
    return 0;
}

This demonstrates:
	•	Declaring pointers
	•	Assigning memory addresses
	•	Dereferencing pointers to read/write values

⸻

🧠 Concept Summary
	•	Pointers store addresses—not values
	•	The * operator dereferences a pointer (go to that address)
	•	The & operator gets the address of a variable
	•	Pointers are used throughout operating systems: in memory, process management, hardware interfaces, and system calls

Mastering pointers opens the door to understanding everything from dynamic memory to kernel internals.

---

Here is Chapter 7: Dynamic Memory with malloc and free, based on your lecture transcript. All code blocks are explicitly closed with triple backticks.

⸻


## Chapter 7: Dynamic Memory with `malloc` and `free`

Up to this point, we’ve declared variables with fixed sizes at compile-time. But what if we don’t know how many values we’ll need to store until runtime?

This is where **dynamic memory allocation** comes in.

---

### 💡 The Problem

Imagine you're writing a program to collect test scores from users. You don’t know how many scores they'll input. One approach is to make a really large array “just in case”—but that wastes memory.

Instead, we can request memory from the operating system **while the program is running** using:

- `malloc()` to allocate memory
- `free()` to release it

---

### 🧠 What Is `malloc`?

`malloc` stands for **memory allocation**. It asks the OS for a chunk of memory of a specified size and returns a **pointer** to that memory.

```c
int *p = malloc(sizeof(int));

	•	sizeof(int) returns the number of bytes needed to store an integer (usually 4).
	•	malloc returns the address of the first byte in that block.
	•	p is now a pointer to this new memory block.
```
---

### 🔐 Always Check for `NULL`

If `malloc` fails (e.g., not enough memory), it returns `NULL`. Always check:

```c
if (p == NULL) {
    printf("Sorry, malloc failed.\n");
    return 1;
}

```
⸻

💾 Storing a Value

You can now store a value at the allocated address:

*p = 42;

This stores the number 42 in the memory block pointed to by p.

To print it:

printf("Value at p: %d\n", *p);


⸻

🧼 Cleaning Up with free

When you’re done using dynamically allocated memory, you must free it:

free(p);

Failing to do this causes a memory leak—unused memory is never returned to the OS. This can degrade performance or crash long-running programs.

⸻

🧪 Example Program
```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *p = malloc(sizeof(int));

    if (p == NULL) {
        printf("Sorry, malloc failed.\n");
        return 1;
    }

    *p = 42;
    printf("Value at p: %d\n", *p);

    free(p);
    return 0;
}
```

Compile with:

gcc malloc.c -o malloc

Then run:

./malloc

You should see:

Value at p: 42

---

### 🛠️ Summary

- `malloc(n)` requests `n` bytes of memory and returns a pointer to it.
- Always check if the result is `NULL`.
- Use the returned pointer to store and access data.
- Always `free()` dynamically allocated memory when you're done.

Neglecting to free memory leads to memory leaks—like borrowing books and never returning them. Eventually, the system runs out of memory to lend.

---

Here is Chapter 8: Stack vs. Heap, Part II, based on your lecture transcript. All code blocks are properly formatted and closed with triple backticks.

⸻


## Chapter 8: Stack vs. Heap, Part II

In this chapter, we dig deeper into the fundamental differences between stack and heap memory in C—especially when working with arrays. You'll see why returning arrays from functions usually requires dynamic memory allocation, and how this relates to the memory lifecycle of your program.

---

### 🧱 The Problem with Returning Arrays

C doesn’t allow functions to return arrays directly, because arrays are not first-class values—they decay into pointers and are tied to the **stack frame** where they were defined.

```c
int* return_array() {
    int r[5] = {1, 2, 3, 4, 5};
    return r;  // 🚫 Warning: returning address of local variable
}
```
This won’t work. The array r is created on the stack, and once the function returns, its memory is deallocated—leaving you with a dangling pointer.

⸻

🔁 The Stack: Fast but Temporary
	•	Stores function call frames and local variables.
	•	Follows a LIFO (last-in, first-out) structure.
	•	Automatically managed: when a function exits, its frame is popped off the stack.
	•	You cannot return variables that were declared on the stack.

⸻

♻️ The Heap: Persistent but Manual

To safely return an array, you must allocate memory on the heap, which persists after the function returns.

#include <stdlib.h>

int* return_array() {
    int* r = malloc(5 * sizeof(int));
    if (r == NULL) return NULL;

    for (int i = 0; i < 5; i++) {
        r[i] = i;  // Fill with values 0 to 4
    }
    
    return r;
}

This way, the array remains valid in the caller’s scope. But now, you are responsible for freeing it.

⸻

✅ Full Example: Returning an Array Safely

#include <stdio.h>
#include <stdlib.h>

int* return_array() {
    int* r = malloc(5 * sizeof(int));
    if (r == NULL) {
        printf("Memory allocation failed.\n");
        return NULL;
    }

    for (int i = 0; i < 5; i++) {
        r[i] = i + 1;
    }
    
    return r;
}

int main() {
    int* my_array = return_array();
    if (my_array == NULL) return 1;

    printf("Values in the returned array:\n");
    for (int i = 0; i < 5; i++) {
        printf("my_array[%d] = %d\n", i, my_array[i]);
    }
    
    free(my_array);
    return 0;
}


⸻

📦 Clarifying Array Syntax

Be careful: int *r = malloc(...); is not the same as int *r[5];.
	•	int *r is a pointer to an int
	•	int *r[5] is an array of 5 pointers to int

They look similar but behave very differently.

⸻

🧠 Visualizing the Stack and Heap

Let’s say we try to return this:

int r[5] = {1, 2, 3, 4, 5};
return r;

What happens?
	1.	Function gets called: stack frame is created
	2.	r lives on the stack
	3.	Function returns: stack frame is destroyed
	4.	r is gone

So the pointer returned points to memory that no longer exists.

Instead, this works:

int* r = malloc(5 * sizeof(int));
return r;

Now the memory lives on the heap and persists until you free() it.

⸻

🧠 Concept Summary
	•	Arrays declared in functions live on the stack and cannot be returned
	•	Heap-allocated arrays persist beyond the function’s scope
	•	Always free() heap memory when you’re done with it
	•	Use pointers to interact with heap memory

Understanding the stack and heap is essential to mastering memory management and data structure design in C.

---

Here is Chapter 9: Stack vs. Heap, Part III, based on your lecture transcript. All code blocks are properly formatted and closed.

⸻


## Chapter 9: Stack vs. Heap, Part III

In this final part of our stack vs. heap series, we tie together all the memory layout concepts and show you how the OS and C compiler enforce rules through memory segmentation. We’ll diagram the full layout of memory in a running C program and explore both theoretical and practical implications.

---

### 🧭 Memory Layout Overview

Let’s map out the memory regions of a typical C program from **high** to **low** addresses:

- **High Memory**
    - Environment variables
    - Command-line arguments
    - Stack (grows downward)
    - (Gap)
    - Heap (grows upward)
    - .bss (zero-initialized globals)
    - .data (initialized globals)
    - .text (code)
- **Low Memory**

Memory grows from both ends and meets in the middle. If the stack and heap collide, your program will crash.

---

### 🧱 Stack Recap

The stack:

- Stores function frames, local variables, and return addresses
- Grows **downward**
- Is fast and automatically managed
- Is scoped to the current function
- Is erased when the function exits

Example:

```c
void greet(int age, char initial) {
    printf("Age: %d, Initial: %c\n", age, initial);
}

Calling greet(37, 'T') puts age and initial on the stack. When greet() returns, those values are gone.

---

### ❌ Returning Stack Memory (Don’t Do This)

You can't safely return the address of a stack variable:

```c
int* bad_function() {
    int x = 42;
    return &x;  // 🚫 ERROR: x is on the stack
}

This code compiles, but the pointer becomes invalid after the function returns. Using it results in undefined behavior.

---

### 🧩 The Heap Revisited

Use the heap when:

- You need memory that persists beyond the current function
- The size is user-defined or large
- You want manual control

Example:

```c
int* create_array() {
    int* r = malloc(5 * sizeof(int));
    if (r == NULL) return NULL;

    for (int i = 0; i < 5; i++) {
        r[i] = i;
    }

    return r;
}

In main():

int* data = create_array();
for (int i = 0; i < 5; i++) {
    printf("%d\n", data[i]);
}
free(data);
```
---

### 🧪 Debugging with `valgrind`

If you forget to call `free()`:

```c
int* leak = malloc(5 * sizeof(int));
// forgot to free(leak);
```
Run this under valgrind:

valgrind ./your_program

You’ll see a memory leak warning like:

20 bytes in 1 blocks are definitely lost

When you free(leak);, valgrind will report:

All heap blocks were freed -- no leaks are possible


⸻

🧠 Summary
	•	The stack is fast, scoped, and OS-managed—but temporary
	•	The heap is flexible, persistent, and user-managed—but dangerous if misused
	•	Returning pointers to stack memory causes undefined behavior
	•	Tools like valgrind help detect memory leaks
	•	Pointers are the bridge between the stack and the heap

Mastering the structure of memory in C is your first real step into systems-level programming and writing reliable, powerful software.

---

## Chapter 11: Function Pointers and Memory Layout in C

Function pointers allow us to store and use the address of a function in a variable, enabling more dynamic and flexible behavior in C programs. They are especially important in systems programming, callbacks, and building abstract interfaces.

---

### 🧠 What Is a Function Pointer?

A **function pointer** is a variable that stores the memory address of a function.

```c
void hello() {
    printf("Hello!\n");
}

void (*func_ptr)() = hello;
func_ptr(); // calls hello()
```

---

### 🧮 Declaring and Using Function Pointers

Basic syntax:

```c
return_type (*pointer_name)(parameter_types);
```

Example with parameters:

```c
int add(int x, int y) {
    return x + y;
}

int (*op)(int, int) = add;
printf("%d\n", op(2, 3)); // prints 5
```

---

### 🧰 Why Use Function Pointers?

- To call different functions at runtime (dynamic dispatch)
- To implement callbacks
- To simplify function tables (jump tables)
- To build interpreters, command dispatchers, and plugins

---

### 📦 Example: Function Pointer Array

```c
#include <stdio.h>

void greet() {
    printf("Hello!\n");
}

void warn() {
    printf("Be careful!\n");
}

void goodbye() {
    printf("Goodbye!\n");
}

int main() {
    void (*actions[3])() = {greet, warn, goodbye};

    for (int i = 0; i < 3; i++) {
        actions[i](); // calls each function in order
    }

    return 0;
}
```

---

### 🧠 Where Do Function Pointers Live?

Function code itself is stored in the **text segment** of memory. When you create a function pointer, you are storing an address in a variable (which likely lives on the **stack** or **data segment**), but that address points to the code in the **text segment**.

---

### 🔍 Function Pointer Syntax Gotchas

Declaring vs. calling:

```c
int (*fp)(int, int); // declaration
fp = add;            // assignment
int result = fp(2, 3); // call
```

If you write:

```c
*fp(2, 3); // ❌ invalid — this tries to dereference the result, not the pointer
```

You need the parentheses:

```c
(*fp)(2, 3); // ✅ correct
```

---

### 🧠 Summary

- Function pointers store addresses to functions
- They are declared using `(*name)(params)` syntax
- Useful for dispatching logic, callbacks, and abstraction
- Stored separately from function code, which lives in the text segment
- Syntax requires care—parentheses matter!

---

## Chapter 12: From Code to Binary — The Compile/Link Cycle

When you write a C program and run it, you're actually going through several hidden steps. This chapter walks through how your source code is transformed into an executable binary that your operating system can run.

---

### 🧱 The Big Picture

C programs go through **four main stages**:

1. **Preprocessing** – Handles `#include`, `#define`, and macros
2. **Compilation** – Translates `.c` source into assembly (`.s`)
3. **Assembly** – Converts assembly into machine code (`.o`)
4. **Linking** – Combines object files into a full executable

---

### 🔍 Stage 1: Preprocessing

```bash
gcc -E hello.c -o hello.i
```

- Removes comments
- Inserts header file contents
- Expands macros
- Output is a `.i` file

---

### ⚙️ Stage 2: Compilation

```bash
gcc -S hello.i -o hello.s
```

- Translates `.i` into assembly (`.s`)
- Human-readable but low-level
- Each function becomes a sequence of instructions

---

### 🔩 Stage 3: Assembling

```bash
gcc -c hello.s -o hello.o
```

- Turns `.s` into machine code object file (`.o`)
- Not yet executable on its own
- Contains binary representations of your functions and data

---

### 🔗 Stage 4: Linking

```bash
gcc hello.o -o hello
```

- Combines `.o` files with libraries
- Resolves symbols (`main`, `printf`, etc.)
- Produces final executable (`hello`)

---

### 📦 Try It: Step-by-Step Compilation

You can run each stage manually:

```bash
gcc -E hello.c -o hello.i
gcc -S hello.i -o hello.s
gcc -c hello.s -o hello.o
gcc hello.o -o hello
```

Then run:

```bash
./hello
```

This gives you a clearer picture of what the compiler is doing under the hood.

---

### 🔍 Where Are These Files?

| File       | Purpose                            |
|------------|------------------------------------|
| `hello.c`  | Your original source code          |
| `hello.i`  | Preprocessed source                |
| `hello.s`  | Assembly version                   |
| `hello.o`  | Machine code (object file)         |
| `hello`    | Final executable                   |

---

### 🧠 Summary

- Compilation is not a single step—it’s a **pipeline**
- Each stage transforms the code closer to machine instructions
- Knowing these stages helps debug errors and optimize programs
- The `gcc` compiler can stop at any stage with flags like `-E`, `-S`, and `-c`

---

## Chapter 13: Introduction to x86 Assembly

Assembly language is the bridge between human-readable code and machine instructions. In this chapter, we’ll focus on the **x86-64 architecture**, which powers most modern desktop and laptop CPUs. You’ll learn basic syntax, instructions, and how to understand what your C code compiles into.

---

### 🧱 What Is Assembly?

Assembly is a **low-level programming language** that maps almost 1-to-1 with machine instructions. Each command directly corresponds to an operation the CPU can perform.

- It’s **platform-specific**
- It requires detailed understanding of **registers**, **memory**, and **calling conventions**
- It offers **ultimate control**, but at the cost of **readability and complexity**

---

### 🧠 Registers in x86-64

Registers are tiny, fast storage locations inside the CPU.

| Register | Purpose                   |
|----------|---------------------------|
| `rax`    | Accumulator (return values) |
| `rbx`    | Base register (callee-saved) |
| `rcx`    | Counter for loops          |
| `rdx`    | Data                       |
| `rsi`    | Source for `mov`/args      |
| `rdi`    | Destination for `mov`/args |
| `rsp`    | Stack pointer              |
| `rbp`    | Base pointer (stack frame) |

Other registers: `r8` to `r15` are general purpose.

---

### 📝 Basic x86 Syntax (AT&T)

AT&T syntax (used by GCC on Linux):

- **Source → Destination**
- Uses `%` for registers and `$` for constants

```asm
mov $5, %rax     # Move constant 5 into rax
add %rbx, %rax   # rax = rax + rbx
```

---

### 🧪 A Simple Example

```asm
.section .data
msg: .asciz "Hello, assembly!\n"

.section .text
.globl _start

_start:
    mov $1, %rax        # syscall: write
    mov $1, %rdi        # file descriptor: stdout
    mov $msg, %rsi      # pointer to string
    mov $17, %rdx       # length of string
    syscall

    mov $60, %rax       # syscall: exit
    xor %rdi, %rdi      # status 0
    syscall
```

---

### 🧮 How to Assemble and Run

Save as `hello.s`, then:

```bash
as -o hello.o hello.s
ld -o hello hello.o
./hello
```

You should see:

```
Hello, assembly!
```

---

### 🔍 C to Assembly

Use `gcc` with `-S` to see the assembly your C code turns into:

```bash
gcc -S hello.c
```

This outputs a `.s` file (assembly), which you can inspect to understand how your C code maps to instructions.

---

### 🧠 Summary

- Assembly exposes the raw instructions sent to the CPU
- x86-64 has a defined set of registers and calling conventions
- AT&T syntax uses `%` and `$` to denote registers and constants
- Writing assembly helps you understand how C really works under the hood

---

# 📘 Lecture 14: Intro to ARM64 Assembly

## ARM64 and Why It Matters

ARM64 is everywhere—your phones, your tablets, your smart devices. It's not just a niche architecture anymore; it's a dominant force in modern computing, and here's why:

- **Mobile Domination**: 100% of smartphones (iOS and Android) run ARM.
- **Embedded and IoT**: From routers to wearables to drones—ARM is the heart.
- **Mac Revolution**: Since 2020, all new Macs use ARM-based chips (M1/M2/M3).
- **Cloud Power**: Amazon's Graviton, Google, Microsoft—all investing in ARM servers.

## Why Learn ARM64?

- Simpler instruction set than x86 (RISC vs. CISC)
- Easier to read and write assembly code
- Better power efficiency and scalability
- Strong ecosystem (GCC, LLVM, Linux, Android)

## 🧠 ARM Architecture Overview

- **31 general-purpose registers**: `X0`–`X30`
- **Stack pointer**: `SP`
- **Zero register**: `XZR`
- **Link register**: `X30` (for return addresses)

### Register Roles
- `X0–X7`: Function/system call arguments
- `X8`: System call number
- `X9–X15`: Caller-saved registers
- `X19–X28`: Callee-saved registers

## 📦 Memory Segments

- `.data`: Initialized static data
- `.bss`: Uninitialized data
- `.text`: Code
- `_start`: Entry point

---

## ✅ Hello World in ARM64 Assembly

### Source: `hello.s`

```asm
.section .data
msg: .asciz "Hello from ARM64!\n"

.section .text
.global _start

_start:
    mov x0, 1              // stdout
    ldr x1, =msg           // message address
    mov x2, 19             // message length
    mov x8, 64             // syscall: write
    svc 0

    mov x0, 0              // exit code
    mov x8, 93             // syscall: exit
    svc 0
```

### Assemble & Run

```bash
as -o hello.o hello.s
ld -o hello hello.o
./hello
```

### Output:
```
Hello from ARM64!
```

---

## 🛠️ How It Works (Step-by-Step)

| Line                        | Meaning                                             |
|----------------------------|-----------------------------------------------------|
| `.asciz "..."`             | Define null-terminated string                       |
| `mov x0, 1`                | Stdout file descriptor                              |
| `ldr x1, =msg`             | Load address of string into `x1`                    |
| `mov x2, 19`               | Length of the string                                |
| `mov x8, 64`               | Syscall number for `write`                          |
| `svc 0`                    | Supervisor call to invoke kernel                   |
| `mov x0, 0`                | Exit code 0 (success)                               |
| `mov x8, 93`               | Syscall number for `exit`                           |
| `svc 0`                    | Exit syscall                                        |

---

## 🧾 Summary

- ARM64 is clean, fast, and easy to learn.
- Much less syntax clutter than x86.
- You’ll use this in Docker via ARM images for future labs.
- Play around, modify the string, try printing multiple lines.

---

## 🙌 Practice Prompt

Change the string to include your name. Reassemble and run it. Try printing two messages in a row using additional syscalls.

---

## Chapter 15: Stack Frames and Calling Conventions

In this chapter, we revisit a foundational concept in system programming: **stack frames**. You’ll learn how functions are managed in memory, how to trace execution with `gdb`, and how recursive calls build up and tear down the call stack.

---

### 🔄 What Is a Stack Frame?

When a function is called:

- A **stack frame** is pushed onto the call stack.
- It contains:
    - Function arguments
    - Local variables
    - Return address (where to continue after the function finishes)

The stack grows **downward** (from high memory to low memory).

#### 📌 Analogy:
Imagine you're working on something and get a phone call. You write down your current task on a sticky note and take the call. Afterward, you refer to the note to continue. That note is your **stack frame**.

---

### 🔍 Viewing Stack Frames with `gdb`

Let’s examine stack behavior in a real C program using `gdb`.

#### `hello.c` Example

```c
#include <stdio.h>

void greet(const char *name) {
    printf("Hello, %s!\n", name);
}

int main() {
    greet("Trevor");
    return 0;
}
```

Compile with debugging info:

```bash
gcc -g -o hello hello.c
```

Run in `gdb`:

```bash
gdb ./hello
(gdb) break greet
(gdb) run
(gdb) backtrace
```

#### 🔎 Backtrace Output

- Shows stack trace from current function to `main`
- Demonstrates Last-In-First-Out (LIFO) structure
- Helps visualize nested function calls

You can also inspect the current frame:

```bash
(gdb) info frame
```

---

### 🔁 Recursion and Stack Frames

#### `count.c`

```c
#include <stdio.h>

void count(int n) {
    printf("%d\n", n);
    if (n > 0)
        count(n - 1);
}

int main() {
    count(3);
    return 0;
}
```

Compile and debug:

```bash
gcc -g -o count count.c
gdb ./count
(gdb) break count
(gdb) run
(gdb) backtrace
```

Each recursive call pushes a new frame. As the function returns, frames are popped off.

---

### 💥 Stack Overflow Demo

Remove the base case from the `count()` function:

```c
void count(int n) {
    printf("%d\n", n);
    count(n - 1); // No base case!
}
```

Result: **Stack overflow** and segmentation fault after too many calls. You’ll see something like:

```
Segmentation fault (core dumped)
```

---

### 📦 Stack Frame Visualization

```
Top of Stack
-------------
count(0)
count(1)
count(2)
count(3)
main()
-------------
Bottom of Stack
```

Each call adds a frame. As calls return, frames are removed in reverse order.

---

### 🧠 Summary

- Each function call creates a **stack frame**
- Stack grows downward and follows **LIFO** behavior
- Use `gdb` to inspect stack frames and debug
- Recursion builds stack frames rapidly; no base case = overflow
- Mastering the stack is essential for debugging, context switching, and system-level programming

---

## Chapter 16: Instruction Flow and Control Logic

Instruction flow is how your program decides what to execute next. Control logic is how it chooses between different paths. Together, they form the backbone of every program’s decision-making and structure.

---

### 🧭 The Program Counter (PC)

The **Program Counter (PC)**, also known as the **Instruction Pointer**, holds the address of the **next instruction** to be executed.

- After executing an instruction, the PC automatically advances
- **Control instructions** (like `jump`, `call`, `ret`) change the PC manually

Think of the PC as the reader's finger moving through lines of code.

---

### 🔀 Control Flow Instructions

Control flow in assembly and machine code comes in two flavors:

1. **Unconditional**
    - Always jumps
    - `jmp` (x86), `b` (ARM)

2. **Conditional**
    - Jumps only if a condition is true
    - `je`, `jne`, `jg`, `jl` (x86)
    - `b.eq`, `b.ne`, `b.gt`, `b.lt` (ARM)

---

### 🧪 Conditional Branch Example (ARM64)

```asm
CMP X0, #0       // Compare X0 with 0
BEQ exit         // If equal, branch to exit

MOV X1, #42      // Otherwise, do something
...
exit:
```

- `CMP` sets flags (Zero, Negative, Carry, Overflow)
- `BEQ` checks the Zero flag (jump if equal)

---

### 🧠 What Is a Flag?

Flags are special bits in a **status register** that describe the result of operations:

- **Z (Zero)**: Result was zero
- **N (Negative)**: Result was negative
- **C (Carry)**: Unsigned overflow
- **V (Overflow)**: Signed overflow

These are set during operations like `CMP` and used in conditional branches.

---

### 💡 Why Is This Useful?

It enables:
- **If/else** structures
- **Loops**
- **Switch-case** logic
- **Error handling and flow control**

Control logic is what turns raw computation into actual decision-making.

---

### 🧱 Examples in C and Assembly

#### C:

```c
if (x == 0) {
    exit(1);
}
```

#### ARM64:

```asm
CMP X0, #0
BEQ exit
```

---

### 🔂 Loops in Assembly

#### C:

```c
for (int i = 0; i < 10; i++) {
    printf("%d\n", i);
}
```

#### Assembly (simplified):

```asm
MOV X1, #0        // i = 0
loop:
CMP X1, #10
BGE end
// body
ADD X1, X1, #1
B loop
end:
```

---

### 🧠 Summary

- The PC tracks the next instruction
- Branch instructions control flow by modifying the PC
- Conditional branches depend on flag values
- Flags are set by arithmetic and logic instructions
- Understanding control flow is key to debugging and writing low-level logic

---

## Chapter 17: Introduction to Processes

In this chapter, we begin our exploration of **processes** in operating systems—what they are, why we need them, and how they work. You’ll see real examples using tools like `htop` and `ps`, learn key concepts like abstraction and virtualization, and understand the life cycle of a process.

---

### 🧠 Abstraction and Virtualization

- **Abstraction**: A simplified view of a complex system.
    - Allows us to use systems without worrying about implementation details.
- **Virtualization**: A specific type of abstraction.
    - Creates the **illusion** of a dedicated machine or system.

For example, Docker containers provide virtual environments that feel isolated, even though they run on the same host OS.

---

### 🧩 What Is a Process?

A **process** is a software object that represents a running program. It includes:
- Program **text** (instructions)
- **Static data** (allocated at compile-time)
- **Dynamic data** (stack, heap)
- **Pending I/O state**
- **Hardware state** (registers, PC, etc.)

**Program** = static file on disk  
**Process** = loaded instance of that program in memory

You can run multiple processes from the same program.

---

### 🛠 Observing Processes with `htop` and `ps`

Install `htop`:

```bash
sudo apt update
sudo apt install htop
```

Run `htop` to see an interactive list of running processes. Alternatively, use:

```bash
ps
```

This lists:
- **PID**: Process ID
- **TTY**: Terminal that created it
- **TIME**: How long it’s been running
- **CMD**: The command that launched it

---

### 🔄 Process Lifecycle: States

Processes move through different states in their lifetime:

| State     | Description                                 |
|-----------|---------------------------------------------|
| **New**   | Just created, not ready to run yet          |
| **Ready** | Loaded and waiting for CPU time             |
| **Running** | Actively executing on the CPU            |
| **Waiting** | Paused until I/O or resource is available |
| **Terminated** | Finished execution, memory released    |

Diagram of transitions:
```
     +--------+     admit      +-------+     dispatch   +---------+
     |  New   |  ------------> | Ready |  ------------> | Running |
     +--------+                +-------+                +---------+
                                   ^                        |
                                   |                        |
              +--------------------+                        |
              |                                             |
              |                 timeout/interrupt           |
              |                                             |
           +------+          I/O request                    v
           |Exit | <-----------------------------+       +--------+
           +------+                              |       | Waiting|
                                                 +-------+--------+
                                                         I/O complete
```

---

### 💡 Concepts Tied to Processes

- **Multitasking**: Running multiple processes by quickly switching between them.
    - Makes it seem like they're running at the same time.
- **Virtual memory**: Each process sees its own memory space.
- **Device abstraction**: OS provides access to hardware without chaos.

---

### 🧠 Definitions

- **Program**: Set of instructions that can be executed.
- **Process**: Instance of a program currently running in memory.

---

### 🧪 Scheduling and the Ready Queue

- Ready processes are stored in a **ready queue**
- Managed in a **First-In, First-Out (FIFO)** structure
- The **scheduler** decides which process runs next
- Processes are assigned a **time slice** (aka quantum)
    - If they don’t finish in time, they are paused and sent back to the queue

---

### ⚠️ Termination

- **Normal exit**: Finishes successfully
- **Abnormal exit**: Crashed, killed, or stopped due to error
- Example: Freezing app that requires Task Manager to kill

---

### 🧠 Summary

- Processes are isolated instances of running programs
- Each process has memory, state, and control logic
- The OS uses abstraction to isolate and manage processes
- Tools like `htop` and `ps` let us inspect what’s running
- Process states model the lifecycle of execution

---

## Chapter 18: Context Switching, System Calls, and the User–Kernel Divide

This chapter dives into how operating systems create the **illusion of multitasking** through **context switching** and how they maintain control via **system calls** and **mode separation**. These are foundational mechanisms that let multiple processes appear to run at the same time—while ensuring security, stability, and efficiency.

---

### 🔄 Context Switching

A **context switch** happens when the CPU stops executing one process and starts another. To do this, the OS must save and restore key information about each process:

- **Program Counter (PC)**: Address of next instruction
- **Register values**
- **Virtual memory mappings**
- **I/O state**
- **Metadata** in the **Process Control Block (PCB)**

This switch is orchestrated by the **scheduler**, a part of the OS that selects the next ready process to run.

> 🧠 Analogy: Like switching between conversations, the CPU "remembers" where it left off and resumes.

#### ⚠️ I/O State

When a process performs an I/O operation (reading a file, waiting for input), the CPU doesn’t sit idle. Instead:

- The process is marked as **waiting**
- Its I/O state is tracked
- The CPU is given to another ready process

This way, the system remains responsive.

---

### 🖥️ Real-Time Example: `htop`

Running `htop` shows processes switching CPU time in real-time. Watch the CPU % usage jump between processes. This visualizes the OS rapidly switching focus thousands of times per second.

> 💡 Context switches cost dozens to hundreds of CPU cycles. OSes work to minimize overhead using **time slices** and smart scheduling.

---

### 🔐 System Calls (Syscalls)

Processes can't directly access hardware. They must ask the OS to act on their behalf—via **system calls**.

#### Common Syscalls

- `read()` – Read from a file/device
- `write()` – Write to a file/device
- `fork()` – Create a new process
- `exec()` – Replace current process with another
- `exit()` – Terminate process
- `wait()` – Wait for a child process to finish

These form the safe "bridges" into the kernel.

---

### 🧪 Example: `fork()` in C

```c
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

int main() {
    pid_t pid = fork();

    if (pid == -1) {
        perror("fork");
        return 1;
    } else if (pid == 0) {
        printf("Hello from the child process. My PID is %d\n", getpid());
    } else {
        printf("Hello from the parent process. My PID is %d and my child is %d\n", getpid(), pid);
    }

    return 0;
}
```

Compile and run:

```bash
gcc -o fork_example fork_example.c
./fork_example
```

---

### 🧱 Behind the Scenes: `fork()`

- A new **PCB** is created
- The parent’s memory space is copied (via **copy-on-write**)
- The new process is placed into the **ready queue**

Both processes now continue independently from the same point.

---

### 🧭 User Mode vs Kernel Mode

| Feature          | User Mode                     | Kernel Mode               |
|------------------|-------------------------------|---------------------------|
| Privileges       | Limited                       | Full system access        |
| Direct hardware? | ❌ No                         | ✅ Yes                    |
| Memory access    | User-space only               | All memory                |
| Stability        | Safe—crashes don’t affect OS  | Dangerous—crashes critical|
| Entry            | Via syscall (`trap` instruction) | Native execution        |

> 🏰 **Analogy**: User mode is like being in a castle courtyard. Kernel mode is like ruling the castle.

---

### 📈 Switching Modes

When a user program needs the OS:

1. A **trap** is triggered (like an interrupt)
2. Control switches to **kernel mode**
3. Kernel performs the requested task
4. Control is returned to **user mode**

---

### 🧠 Summary

- **Context switching** enables multitasking by swapping active processes.
- **System calls** give user programs controlled access to OS services.
- **User mode** is restricted and safe; **kernel mode** is powerful and risky.
- Understanding this divide is key to writing safe, efficient, and stable programs.

---

## Chapter 19: Hardware, the Kernel, and User Processes

This chapter provides a layered view of how modern operating systems abstract the complexity of hardware through kernel control and user processes. We’ll break down each layer from raw hardware to user-facing applications and discuss how the Linux kernel acts as the bridge.

---

### 🧱 The Layered Model of an Operating System

Operating systems use **abstraction** to manage complexity. We break the system into three main layers:

1. **Hardware**
2. **Kernel**
3. **User Processes**

---

### ⚙️ Layer 1: Hardware

The **hardware layer** includes the most fundamental components:

- CPU
- RAM
- Disk
- Network interfaces
- I/O peripherals

This layer is closest to "reality"—the raw metal and circuits.

---

### 🧠 Layer 2: The Kernel

The **Linux kernel** sits directly on top of the hardware. It manages and abstracts:

- **System calls**
- **Process management**
- **Memory management**
- **Device drivers**

The kernel has **full control** over the hardware and provides a secure interface for user programs.

#### Responsibilities:

- Acts as a **guard** and manager
- Ensures **safe memory allocation**
- Schedules **CPU time**
- Translates user requests into hardware actions

---

### 👤 Layer 3: User Processes

This is where user-facing software lives:

- Graphical User Interfaces (GUIs)
- Shells (like `bash`)
- User applications and servers

These run in **user mode**, a restricted environment. Crashes here do **not** crash the whole system.

---

### 🔒 User Mode vs Kernel Mode

| Feature             | User Mode                        | Kernel Mode                    |
|---------------------|----------------------------------|--------------------------------|
| Access              | Limited (safe)                   | Full system access             |
| Memory Isolation    | Enforced                         | Can access all memory          |
| Crash Consequence   | Local to process                 | Can crash the entire system    |
| Purpose             | Run user apps                    | Manage system resources        |

---

### 🛠 Main Memory and Bit Management

Everything in memory—processes, kernel code, drivers—is **just bits**.

- **Main memory** is subdivided by the kernel.
- Each user process gets its own memory space.
- **Swap space** may be used for overflow.

Memory regions may be:
- Read-only
- Private
- Shared (if explicitly allowed)

---

### 🔌 Device Drivers

Device drivers:
- Live in **kernel mode**
- Manage communication with hardware (printers, disks, etc.)
- Cannot be safely managed by user processes

This prevents crashes and ensures system integrity.

---

### 🔁 Process Management and Context Switching

Kernel is responsible for:
- Creating, pausing, resuming, and terminating processes
- Dividing CPU time using **time slices**
- Switching between processes via **context switching**

Steps during a context switch:
1. Timer interrupts process
2. Kernel saves CPU/memory state
3. Kernel handles any tasks
4. Kernel selects next process
5. Prepares memory and CPU
6. Sets time slice duration
7. Switches to user mode

---

### 📞 System Calls (Syscalls)

Syscalls allow user processes to request kernel services.

Examples:
- `fork()` – Create a new process
- `exec()` – Replace process with new one
- `read()`, `write()`, `exit()`, etc.

---

### 🧬 Fork vs Exec

- `fork()` creates an **identical copy** of a process (child).
- `exec()` replaces the calling process with a **new program**.

Typical shell behavior:
1. User enters command
2. Shell `fork()`s
3. Child runs command via `exec()`
4. Parent shell continues running

---

### 🧠 Summary

- The system is layered: **hardware → kernel → user processes**
- The **kernel** controls memory, devices, and process management
- **User mode** is safe; **kernel mode** is powerful and dangerous
- **System calls** allow controlled interaction with the kernel
- Understanding these abstractions is key to systems programming

---

## Chapter 20: `fork()` – Creating New Processes in Unix-like Systems

This chapter focuses on the `fork()` system call, which lies at the heart of multitasking in Unix-like operating systems. By duplicating the currently running process, `fork()` allows programs to spawn child processes, setting the stage for complex behaviors like parallel execution, interprocess communication, and more.

---

### 🧠 What is `fork()`?

- `fork()` is a **system call** that creates a **new process**.
- It is invoked by a user-space program and executed in **kernel mode**.
- The newly created process is called the **child process**.
- The original is the **parent process**.

```c
pid_t pid = fork();
```

- If `pid < 0`: Fork failed
- If `pid == 0`: Code is running in the **child**
- If `pid > 0`: Code is running in the **parent**, and `pid` is the child’s PID

---

### 🔁 Context Switching After `fork()`

After a successful fork:

- Both parent and child processes continue execution from the same point.
- They may not run **simultaneously** (especially on a single-core machine), but the **illusion of concurrency** is created through **context switching**.
- Each process receives its own:
    - Stack
    - Heap
    - Registers
    - Program Counter
    - File Descriptors (copied)

```c
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

int main() {
    pid_t pid = fork();

    if (pid < 0) {
        perror("Fork failed");
        return 1;
    } else if (pid == 0) {
        printf("Hello from the child process. My PID is %d, my parent is %d\n", getpid(), getppid());
    } else {
        printf("Hello from the parent process. Child PID is %d\n", pid);
        wait(NULL);
        printf("Child process finished\n");
    }

    return 0;
}
```

---

### 🧪 Behavior Example: Global Variable Separation

```c
int x = 5;

pid_t pid = fork();

if (pid == 0) {
    x += 5;
    printf("Child x: %d\n", x); // 10
} else {
    printf("Parent x: %d\n", x); // 5
}
```

- Each process gets a **copy** of the address space.
- **Changes in one process do not affect the other.**

---

### 💀 Zombie Processes

A **zombie process** is a child that has terminated but has **not been reaped** by its parent.

- Remains in the process table
- Can be seen with `ps` or `top` as `<defunct>`

To avoid zombies, use:

```c
wait(NULL);
```

Or more precisely for multiple children:

```c
waitpid(child_pid, NULL, 0);
```

---

### ⚠️ Common Fork Mistakes

1. **Not calling `wait()`** – leads to zombies.
2. **Forking inside a loop** – can create thousands of processes if not managed.
3. **Assuming execution order** – Parent and child are scheduled independently; order is **not guaranteed**.

---

### 🧪 Zombie Creation Example

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main() {
    pid_t pid = fork();

    if (pid == 0) {
        // Child exits immediately
        exit(0);
    } else {
        // Parent sleeps, doesn’t call wait()
        sleep(30);
    }

    return 0;
}
```

- During sleep, child is a zombie.

---

### 💥 Zombie Prevention

```c
#include <sys/wait.h>

int main() {
    pid_t pid = fork();

    if (pid > 0) {
        wait(NULL); // Parent waits for child to terminate
    }

    return 0;
}
```

- The system call `wait()` ensures the parent **reaps** the child and frees its entry in the process table.

---

### 🧠 Summary

- `fork()` duplicates a process, creating a child.
- Both processes share the same code but have independent memory.
- Use `getpid()` and `getppid()` to retrieve process IDs.
- Always `wait()` for child processes to prevent zombies.
- The behavior of `fork()` is foundational for multiprocessing, shells, and more.



---



## Chapter 21: Corruption Risks During Context Switches

In this chapter, we examine a subtle but serious challenge in operating system design: **data corruption during context switches**. You’ll learn how process memory and register states can be compromised if not properly isolated, how corruption manifests, and how operating systems mitigate this risk.

---

### 🔄 Recap: What Is a Context Switch?

A **context switch** occurs when the CPU saves the state of the currently running process and loads the state of another.

Each process has its own:
- Register values (e.g., `r0`, `r1`, etc.)
- Stack
- Program Counter (PC)
- Memory mappings

These are saved and restored by the kernel to give the illusion of concurrent execution.

---

### 💥 The Risk of Memory and Register Corruption

If context switches are handled improperly, two processes can **interfere with each other**—especially if memory or registers are not safely isolated.

#### Consider this output:

```
-- Before context switch --
[Process A] r0 = 1, stack = ""
[Process B] r0 = 100, stack = ""

-- Context switch to process A --

-- Context switch to process B --

-- After context switches --
[Process A] r0 = 2, stack = "Process r0 was 1"
[Process B] r0 = 101, stack = "Process r0 was 100"
```

This is **correct behavior**: each process maintains its own values independently.

#### But what if we saw this?

```
-- After context switches --
[Process A] r0 = 2, stack = "Temporary process data."
[Process B] r0 = 101, stack = "Temporary process data."
```

⚠️ That’s a problem. Both processes have the **same stack contents**, which means they’ve either:
- Written to the same memory location
- Used shared or improperly isolated memory
- Experienced register leakage between switches

---

### 🧠 Why Does This Happen?

Improper context isolation can result from:
- **Buggy kernel code**
- **Stack pointer errors** (e.g., reusing the same region)
- **Shared global variables** without proper locking or separation
- **Manual context switching logic** in educational OSes or microkernels

---

### 🛡️ How Real OSes Prevent This

Modern operating systems mitigate corruption risks through:
- Strict **virtual memory mapping** (each process gets its own address space)
- Saving and restoring **registers** during switches
- Kernel-managed **Process Control Blocks (PCBs)** storing:
  - Register states
  - Stack pointers
  - Instruction pointers
- Protected **user–kernel mode separation**
- **Hardware support** for process isolation (e.g., memory management units)

---

### 🔍 Debugging Corruption

When debugging:
- Check for variables leaking between processes
- Verify `r0`, `sp`, or `pc` are saved/restored correctly
- Use tools like `gdb` to inspect memory and stack

---

### 🧠 Summary

- Context switches can introduce memory/register corruption if done incorrectly.
- Each process must maintain **strict isolation** of its execution context.
- Real OSes rely on **virtual memory, PCBs, and hardware isolation** to prevent this.
- You can visualize corruption by observing duplicated stack contents or improper register values.

---



## Chapter 22: Threads vs Processes

In this chapter, we explore one of the most fundamental distinctions in operating system design: **threads** vs **processes**. While they may seem similar at first glance—after all, both represent execution contexts—they behave very differently when it comes to memory, scheduling, and isolation.

---

### 🧠 What Is a Process?

A **process** is an instance of a program in execution. It contains:
- A complete memory space (code, data, heap, stack)
- File descriptors
- Register states
- A Process Control Block (PCB) maintained by the OS

Each process is **isolated** from others—one process can't (normally) access another’s memory directly.

---

### 🧵 What Is a Thread?

A **thread** is a lightweight unit of execution **within a process**. Multiple threads can:
- Share the same memory space (heap, globals)
- Have their own stack and registers
- Communicate more efficiently than processes (no need for IPC)

Threads within the same process are often called **user-level threads** or **POSIX threads (pthreads)**.

---

### 🔄 Comparison Table

| Feature       | Process                            | Thread                                         |
| ------------- | ---------------------------------- | ---------------------------------------------- |
| Memory        | Isolated                           | Shared within process                          |
| Scheduling    | Independently scheduled            | May be scheduled cooperatively or preemptively |
| Crash Scope   | One crash affects only one process | One thread crash may affect whole process      |
| Communication | Uses IPC (slow)                    | Simple shared memory                           |
| Overhead      | High (OS-managed)                  | Lower (can be user-managed)                    |

---

### 🧪 Analogy: Apartments vs. Rooms

- **Processes** are like apartments in a building—each one is separate, has its own key, and doesn't share walls.
- **Threads** are like roommates in the same apartment—separate beds, but shared kitchen and living room. If one starts a fire in the kitchen, everyone’s affected.

---

### 💥 Dangers of Threads

The shared nature of memory in threads makes them **faster** but also more **dangerous**:
- Race conditions can occur when two threads try to update shared data simultaneously
- Synchronization tools like **mutexes**, **semaphores**, and **condition variables** are required
- Bugs are hard to reproduce and debug (heisenbugs)

---

### 🛠️ Practical Use Cases

| Use Case                       | Threads or Processes?         |
| ------------------------------ | ----------------------------- |
| Multi-user web server          | Threads (handle each request) |
| Data-parallel computation      | Threads (shared data)         |
| Isolation between applications | Processes                     |
| Crash resilience               | Processes                     |

---

### ⚙️ C Thread Lifecycle (POSIX Model)

```c
#include <pthread.h>
#include <stdio.h>

void* say_hello(void* arg) {
    printf("Hello from thread!\\n");
    return NULL;
}

int main() {
    pthread_t tid;
    pthread_create(&tid, NULL, say_hello, NULL);
    pthread_join(tid, NULL);
    return 0;
}
```

This code creates a new thread that prints a message, then waits for it to finish.

---

### 🐍 Python Threading Example

Python also supports multithreading using the `threading` module:

```python
import threading

def worker():
    print("Hello from Python thread!")

# Create a thread
t = threading.Thread(target=worker)

# Start and wait for it to finish
t.start()
t.join()
```

This behaves similarly to the C example using `pthread_create`, though it's subject to the **Global Interpreter Lock (GIL)**, which can affect performance in CPU-bound tasks.

---

### 🔍 Python vs C Threads

- **Python threads** are useful for I/O-bound tasks (networking, file I/O)
- **C threads** are better for CPU-bound parallelism (since they’re not limited by the GIL)
- In Python, consider using `multiprocessing` instead of threads for CPU-heavy workloads

---

### ✅ Summary

- **Processes** offer safety and isolation but have higher overhead.
- **Threads** are lightweight and efficient but require careful synchronization.
- Choose the right tool for your task—favor processes for isolation and threads for performance within shared data contexts.

---

## Chapter 23: Go, Goroutines, and Race Conditions

Go (or Golang) is a modern systems-level programming language developed at Google. It emphasizes simplicity, safety, and concurrency. In this chapter, we explore Go's concurrency model, focusing on goroutines and how they compare to traditional threads and processes.

------

### 🧵 What Is a Goroutine?

A **goroutine** is Go's lightweight unit of execution, similar to a thread but more efficient. Goroutines:

- Are managed by the Go runtime rather than the OS
- Start with very small stack sizes (e.g. 2 KB)
- Are multiplexed onto a small number of OS threads
- Can number in the thousands or millions

You create a goroutine by using the `go` keyword before a function call:

```go
go doSomething()
```

This spawns a new concurrent execution of `doSomething()`.

------

### ⛓️ Threads vs Goroutines vs Processes

| Feature          | Process      | Thread        | Goroutine                  |
| ---------------- | ------------ | ------------- | -------------------------- |
| Memory Isolation | Isolated     | Shared        | Shared (within Go process) |
| Managed By       | OS           | OS            | Go Runtime                 |
| Cost             | High         | Moderate      | Low                        |
| Scheduling       | OS Scheduler | OS Scheduler  | Go Scheduler               |
| Communication    | IPC (slow)   | Shared memory | Channels                   |

------

### 📦 Packages: `time` and `sync`

Go's standard library provides useful packages for managing concurrency:

- `time.Sleep()` can delay execution
- `sync.WaitGroup` allows synchronization (waiting for goroutines to finish)

Example:

```go
package main
import (
    "fmt"
    "sync"
    "time"
)

func sayHello(wg *sync.WaitGroup) {
    defer wg.Done()
    fmt.Println("Hello from goroutine")
    time.Sleep(time.Second)
}

func main() {
    var wg sync.WaitGroup
    wg.Add(1)
    go sayHello(&wg)
    wg.Wait()
    fmt.Println("Done")
}
```

------

### 🧠 Race Conditions

A **race condition** occurs when two or more goroutines access shared memory simultaneously, and at least one is writing.

Example:

```go
package main
import (
    "fmt"
    "sync"
)

var x = 0

func increment(wg *sync.WaitGroup) {
    for i := 0; i < 1000; i++ {
        x++
    }
    wg.Done()
}

func main() {
    var wg sync.WaitGroup
    wg.Add(2)
    go increment(&wg)
    go increment(&wg)
    wg.Wait()
    fmt.Println("x:", x)
}
```

This program may print different results each time, such as `x: 1863`, `x: 2000`, or something in between. That inconsistency is due to a race condition.

Use `go run -race your_program.go` to detect race conditions.

------

### 🛡️ Preventing Race Conditions

Go provides the `sync.Mutex` type to protect critical sections:

```go
var mu sync.Mutex

mu.Lock()
x++
mu.Unlock()
```

You can also use atomic operations or channels to coordinate safely between goroutines.

------

### ✅ Summary

- **Goroutines** are Go's concurrency primitive: lightweight, efficient, and managed by the runtime.
- **WaitGroups** help coordinate goroutines.
- **Race conditions** are a common concurrency bug—detectable using `-race` and preventable using mutexes or safe design.

Concurrency is a core part of Go. Understanding goroutines and synchronization is essential for writing correct and scalable Go programs.

---

## Chapter 24: Visualizing Thread Execution with Python and `htop`

In this chapter, we explore how to observe and understand thread-level concurrency using Python and the Unix utility `htop`. This chapter connects practical programming exercises with real-time system-level monitoring.

------

### 🧵 Python Threads Recap

Python threads are created using the `threading` module. Threads share memory and are used primarily for I/O-bound tasks due to Python's Global Interpreter Lock (GIL).

```python
import threading

def cpu_task():
    while True:
        pass  # Busy wait to simulate CPU work

for _ in range(4):
    t = threading.Thread(target=cpu_task)
    t.daemon = True
    t.start()
```

This code starts four infinite threads that burn CPU.

------

### 🖥️ Monitoring with `htop`

`htop` is a powerful system monitor for Unix systems that allows you to:

- View per-thread CPU usage
- Observe memory consumption
- See process tree hierarchies

Launch `htop` and press `H` to toggle thread view.

You should see multiple entries under your Python process, each representing a thread.

------

### 🔍 Why Threads May Not Use All CPUs

Due to Python’s **Global Interpreter Lock (GIL)**, only one thread can execute Python bytecode at a time.

- Even with multiple threads, CPU-bound programs may only use a single core.
- Use `multiprocessing` for CPU-bound tasks if true parallelism is needed.

------

### 🧪 Experiment: Threads in Action

1. Run the thread script in a terminal.
2. In another terminal, launch `htop`.
3. Press `H` to enable thread view.
4. Observe CPU usage by thread.

Questions:

- How many threads does Python actually start?
- Does CPU usage increase with more threads?
- How does `htop` visualize the load?

------

### 🛠️ Alternative: Multiprocessing

For actual parallelism:

```python
from multiprocessing import Process

def cpu_task():
    while True:
        pass

for _ in range(4):
    p = Process(target=cpu_task)
    p.start()
```

Each process runs in its own memory space and bypasses the GIL.

------

### ✅ Summary

- Python threads are great for I/O but limited by the GIL for CPU-bound tasks.
- `htop` helps you visualize system-level activity down to individual threads.
- Use `multiprocessing` to utilize multiple cores effectively.

Understanding the real system behavior of your concurrent programs is essential. Tools like `htop` bridge the gap between code and CPU.

---

## **Chapter 25: Intro to Scheduling and the Round-Robin (RR) Algorithm**





CPU scheduling is one of the most fundamental mechanisms in an operating system. When multiple processes are ready to run, the OS must decide which one gets to use the CPU next. This decision-making process is known as **scheduling**.



In this chapter, we focus on one of the most common and intuitive scheduling algorithms: **Round-Robin (RR)**.



------





### **🕰️ What Is Scheduling?**





Scheduling determines the order in which processes access the CPU. Key goals include:



- **Fairness**: every process should get CPU time
- **Efficiency**: keep the CPU busy
- **Response time**: especially important in interactive systems





Schedulers can be **preemptive** (a process can be interrupted) or **non-preemptive** (a process runs until it yields or finishes).



------





### **🔁 Round-Robin Scheduling**





Round-robin is a preemptive scheduling algorithm designed for **time-sharing systems**. Each process gets a fixed time slice (called a **quantum**) and is cycled through in a queue.





#### **How it works:**





1. All processes are placed in a ready queue.
2. The scheduler picks the first process in the queue.
3. That process runs for a maximum of quantum milliseconds.
4. If the process doesn’t finish, it’s put at the end of the queue.
5. The next process is selected, and the cycle continues.





This ensures **fair access** and **regular rotation** among all processes.



------





### **🧠 Example:**





Suppose we have 3 processes:



- P1: needs 5ms total
- P2: needs 3ms total
- P3: needs 8ms total





With a time quantum of 2ms, the RR sequence might look like:

```
P1 (2ms) → P2 (2ms) → P3 (2ms) → P1 (2ms) → P2 (1ms) → P3 (2ms) → P1 (1ms) → P3 (2ms)
```

The processes take turns, and none hogs the CPU.



------





### **⏱️ Choosing the Quantum**





The choice of quantum size is crucial:



- Too small: too many context switches (wasteful)
- Too large: behaves like First-Come, First-Served (loses interactivity)





Typical quanta: 10ms to 100ms on modern systems.



------





### **🛠️ Implementing RR**





In real systems, RR is often implemented with **process control blocks (PCBs)** and a **circular queue**.



Each context switch involves:



- Saving the current process state
- Restoring the next process’s state





A timer interrupt signals the end of a time slice.



------





### **🔄 RR vs Other Schedulers**



| **Feature**   | **Round-Robin** | **FCFS** | **Priority Scheduling**       |
| ------------- | --------------- | -------- | ----------------------------- |
| Preemptive    | Yes             | No       | Yes (can be)                  |
| Fairness      | High            | Low      | Varies                        |
| Response Time | Good            | Poor     | Poor (for low-priority tasks) |
| Complexity    | Low             | Very low | Moderate                      |



------





### **✅ Summary**





- **Scheduling** determines which process runs next.
- **Round-robin** rotates processes through fixed time slices.
- It balances fairness and responsiveness, ideal for time-sharing.
- Choosing the right quantum is key to performance.





Understanding RR gives a foundation for exploring more advanced algorithms like Multilevel Feedback Queues and Shortest Remaining Time First.



---

## Chapter 26: Scheduling Algorithms

In this chapter, we survey a variety of common **CPU scheduling algorithms** and how they trade off fairness, efficiency, and responsiveness. Building on Round-Robin from the previous chapter, we now explore **First-Come First-Served (FCFS)**, **Shortest Job First (SJF)**, **Shortest Remaining Time First (SRTF)**, and **Multilevel Feedback Queues (MLFQ)**.

------

### 🧭 The Goals of Scheduling

Schedulers aim to:

- Maximize CPU utilization
- Minimize turnaround time and waiting time
- Ensure fairness among processes
- Maintain responsive behavior (especially for interactive tasks)

Different algorithms prioritize different goals.

------

### 1️⃣ First-Come First-Served (FCFS)

- **Non-preemptive**
- Processes run in the order they arrive

Advantages:

- Simple to implement
- Predictable

Disadvantages:

- **Convoy effect**: long jobs delay shorter ones
- Poor average response time

------

### 2️⃣ Shortest Job First (SJF)

- **Non-preemptive**
- Chooses process with the shortest **total expected CPU burst**

Advantages:

- Minimizes average waiting time

Disadvantages:

- Requires knowledge of future job lengths
- Can lead to starvation of long jobs

------

### 3️⃣ Shortest Remaining Time First (SRTF)

- **Preemptive** version of SJF
- A new process can preempt if it has a shorter remaining time

Advantages:

- Even better average waiting time than SJF

Disadvantages:

- High overhead from frequent context switches
- Needs accurate estimates of burst time

------

### 4️⃣ Round-Robin (RR)

- Reviewed in Chapter 25
- Equal time slices (quanta)
- Cycles through processes

Advantages:

- Fair and responsive
- Simple implementation

Disadvantages:

- Too small a quantum causes overhead
- Too large a quantum reduces responsiveness

------

### 5️⃣ Multilevel Feedback Queues (MLFQ)

- A **dynamic and adaptive** scheduling method
- Processes are grouped into multiple queues, each with different priority and time slice lengths
- Jobs can **move between queues** based on behavior (e.g. CPU-bound vs I/O-bound)

#### Key features:

- Processes start at high-priority queues
- If they use too much CPU, they’re demoted
- If they wait too long, they may be promoted

Advantages:

- Good for interactive and batch processes
- Very flexible

Disadvantages:

- Complex to implement and tune
- Can be difficult to understand scheduling decisions

------

### 🧪 Simulation Activity (Optional)

Try simulating each of these algorithms with a fixed set of jobs and burst times. Use a Gantt chart to visualize execution order and calculate:

- Average waiting time
- Average turnaround time

Example job set:

- P1: 6ms
- P2: 8ms
- P3: 7ms
- P4: 3ms

------

### ✅ Summary

| Algorithm   | Preemptive | Responsive | Starvation Risk | Notes                           |
| ----------- | ---------- | ---------- | --------------- | ------------------------------- |
| FCFS        | No         | Poor       | Low             | Simple but causes convoy effect |
| SJF         | No         | Poor       | High            | Optimal but impractical         |
| SRTF        | Yes        | Moderate   | High            | Good performance, more overhead |
| Round-Robin | Yes        | Good       | Low             | Fair and widely used            |
| MLFQ        | Yes        | High       | Medium          | Adaptive and powerful           |

Choosing the right scheduler depends on your system’s goals and workload. In practice, modern OSes use hybrids that combine several of these techniques.

---

## Chapter 27: Scheduling Algorithm Evaluation

After studying individual scheduling algorithms, we now turn our attention to **evaluating** them. This chapter will introduce the metrics and methods used to assess scheduling policies, including theoretical and experimental comparisons.

------

### 📏 Key Evaluation Metrics

Schedulers are often compared based on the following criteria:

- **CPU Utilization**: Percentage of time the CPU is doing useful work.
- **Throughput**: Number of processes completed per unit time.
- **Turnaround Time**: Time from submission to completion.
- **Waiting Time**: Time spent in the ready queue.
- **Response Time**: Time from submission to first response (important for interactive systems).

Different workloads may prioritize different metrics.

------

### 🧠 Trade-Offs and Priorities

Improving one metric can harm another. For example:

- Maximizing throughput may reduce fairness.
- Minimizing waiting time may increase response time variance.
- Low turnaround time for short jobs may starve longer ones.

These trade-offs are central to scheduler design.

------

### 🧪 Simulation-Based Evaluation

You can simulate the behavior of schedulers with a fixed set of processes. For example:

#### Process Set:

- P1: 0ms arrival, 10ms burst
- P2: 2ms arrival, 5ms burst
- P3: 4ms arrival, 2ms burst

Try simulating:

- FCFS
- SJF
- SRTF
- Round-Robin (quantum = 3ms)
- MLFQ

Use a Gantt chart and calculate:

- Average turnaround time
- Average waiting time
- Context switches

------

### 📊 Visualization and Tools

Tools like Excel, Google Sheets, or custom Python scripts can help plot Gantt charts or calculate averages.

Example Python pseudocode:

```python
# Simple simulation loop structure
for time in range(0, max_time):
    select_next_process()
    run_for_one_tick()
    record_metrics()
```

------

### 🔄 Real-World Constraints

In real systems, other factors complicate evaluation:

- I/O wait times
- Interrupts
- Priority inversion
- Cache effects
- Hardware support (e.g. context switch time)

Thus, empirical benchmarks and profiling are often used in addition to simulations.

------

### ✅ Summary

- **Scheduler evaluation** is about balancing multiple metrics.
- Simulations provide controlled comparisons.
- Real-world systems must account for additional complexity.
- No scheduler is perfect—choose based on workload and system goals.

Evaluating algorithms rigorously allows designers to understand not just what works, but **why** and **under what circumstances**.
