# CSI 2372 - Final Exam - Cheat Sheet

## Question 1-5 (4 points each)
The first five questions will be True/False, Multiple Choice, and/or Multiple Selection

## Question 6 (6 points)
Assesses your memory management skills by requiring a C++ code realization based on a provided description.

### Topic List

#### Dynamic Memory Allocation

```cpp
#include <iostream>

int* pointVar;
pointvar = new int; // for initializing to a new variable.

int *differentVar = new int; // alternate way of declaring new.

int x = 420;
int *pointx = &x; // use & to declare pointer to a preexisting variable


```

```cpp
int main() {
    // Initialize a matrix, 4 rows, 3 columns. Each element of the array of size 4 contains an array of size 3.
    int matrix[4][3] = { {11, 12, 13}, {14, 15, 16}, {17, 18, 19}, {110, 111, 112} };
 // Create a pointer to the second row of the matrix, index 1
 // This a pointer to an array of size 3
 // The brackets are needed () for array pointer declaration
 // pointer name is arraypoint
 int(*arraypoint)[3] = &matrix[1]; // Points to the second row (index 1)
 // Access the values at the addresses of individual elements in the second row
 int value_1 = (*arraypoint)[0]; // int address_1 = &(*ptr)[0]; for address of this pointer
 int value_2 = (*arraypoint)[1]; // int address_2 = &(*ptr)[1]; for address of this pointer
 int value_3 = (*arraypoint)[2]; // int address_3 = &(*ptr)[2]; for address of this pointer
 // Print the values
 std::cout << "Value at Matrix[1][0]: " << value_1 << std::endl;
 std::cout << "Value at Matrix[1][1]: " << value_2 << std::endl;
 std::cout << "Value at Matrix[1][2]: " << value_3 << std::endl;
}
```

#### Smart Pointers

##### Unique Pointer
Type of smart pointer in C++ that represents exclusive ownership of a dynamically allocated object. Unlike shared pointers, only one unique pointer can own the object, and when the unique pointer goes out of scope, the associated memory is automatically deallocated.

```cpp
#include <memory>

int main() {
    std::unique_ptr<int> uniqueInt = std::make_unique<int>(42);
    // uniqueInt cannot be copied, only moved.
    
    // Attempting to assign it to another unique pointer will result in a compilation error
    // std::unique_ptr<int> uniquePtr2 = uniquePtr1;  // Error: copy constructor is deleted
    
    // Move ownership to another unique pointer
    std::unique_ptr<int> uniqueInt2 = std::move(uniqueInt1);

    // Attempting to access the original unique pointer after the move
    // This will result in undefined behavior, as the ownership has been transferred
    // std::cout << *uniquePtr1 << std::endl;  // Undefined behavior

    // Accessing the new unique pointer
    std::cout << *uniquePtr2 << std::endl;  // Valid

    return 0;  // uniqueInt is automatically deallocated when it goes out of scope
}
```

#### Shared Pointer
Type of smart pointer in C++ that allows multiple shared pointers to share ownership of the same dynamically allocated object. Memory is automatically deallocated when the last shared pointer that owns it goes out of scope, preventing premature deallocation.

```cpp
#include <memory>

int main() {
    std::shared_ptr<int> sharedInt = std::make_shared<int>(42); //1 Instance
    // sharedInt can be copied, and all copies share ownership
    
    {
        std::shared_ptr<int> sharedInt2 = sharedInt; //2 Instances
    } //1 Instance (sharedInt)
    return 0;  // sharedInt is automatically deallocated when all of them go out of scope
}//0 Instances
```



#### Memory Deallocation 
#### Memory Pool (Probably Not)



## Question 7 (12 points)
evaluates your ability to provide access to reading and writing files with some specifications. 

### Reading From Files 

### Writing From Files 

### File Security 

#### File Permission Constants: 

- S_IRUSR (user read)
- S_IWUSR (user write)
- S_IXUSR (user execute)
- S_IRGRP (group read)
- S_IWGRP (group write)
- S_IXGRP (group execute)
- S_IROTH (others read)
- S_IWOTH (others write)
- and S_IXOTH (others execute)


### Streams 

### Cursor Manipulation 


## Question 8.1-8.3 + 8.4 bonus (6 points each + 6 point bonus)
Code related to links and nodes, divided into three segments, each worth 6 points. There's a bonus for those who complete the entire code, in addition to the required three segments. The main method, crucial for the bonus, must yield specified outputs (but it is optional). Completing only the three segments earns 18 points, and the bonus carries a weight of 6 points.

A linked list is a collection of nodes. Each node has two parts: data and a reference to the next
node. Unlike arrays, linked lists don't require contiguous memory allocation. They can easily grow
or shrink during runtime. Common types of linked lists include:
➢ Singly linked lists (each node points to the next),
➢ Doubly linked lists (each node points to both the next and previous), and
➢ Circular linked lists (the last node points back to the first).


## Question 9 (18 points)
three segments focusing on adding and removing observers for different events. Your ability to complete tasks with specific constructors and classes will be evaluated. 

### Observer Pattern 

![](http://csi2372.rambolps.ca:3000/uploads/98acf8c1-6ba3-4305-bc4e-a63c60e02feb.png)

## Question 10.1-10.2 (6 points + 14 points)


covers the logic of a JK flip-flop in two segments: the first involves implementation and logic/schematic (6 points), while the second assesses your ability to write a C++ code for an 8-bit binary counter using a JK flip-flop. Be prepared for either synchronous (iteration of 0 to 255 binary) or asynchronous (event-driven) scenarios. This segment is worth 14 points.

### SR Flip Flop 
![](http://csi2372.rambolps.ca:3000/uploads/33ecf4df-0c6a-49b4-904e-e28d7f0e0c10.png)

### JK Flip Flop 

![](http://csi2372.rambolps.ca:3000/uploads/317fda94-3cba-47cf-b560-fbf517835c52.png)

#### Code 
![](http://csi2372.rambolps.ca:3000/uploads/ed622ece-43c5-4753-bf38-78306f7d81de.png)

![](http://csi2372.rambolps.ca:3000/uploads/db45868d-39f3-4a1d-9794-6299b8bc0eab.png)

![](http://csi2372.rambolps.ca:3000/uploads/a70df603-ff69-4e5c-9517-0ba63e1549de.png)

#### Timing Diagram 

![](http://csi2372.rambolps.ca:3000/uploads/0a529f1e-0021-4e7f-85e8-352d7e4e3fbb.png)

Positively Edged Triggered (So output can only change when the clock moves from low to high)
When Set is High, Output is High Priority) 
When Reset is High, Output is Low Priority

When J and K are High = Toggle the Output 
When J and K are Low = No Change 
When J is High and K is Low Q = 1
When K is High and J is Low  Q = 0

![](http://csi2372.rambolps.ca:3000/uploads/162454b3-d51e-4de1-9825-59757ab81d5e.png)

#### 8 Bit Counter 

An 8-bit counter implemented using JK flip-flops is a circuit that counts in binary from 00000000 to 11111111 (0 to 255 in decimal). To create an 8-bit counter, we need eight JK flip-flops, one for each bit. The JK flip-flop is a type of flip-flop that can toggle its output based on the inputs.

![](http://csi2372.rambolps.ca:3000/uploads/4b01bc3a-ef44-44d7-bea1-a1644a5990b0.png)

### JK Flip Flop 
```cpp 

#include <iostream>

class JKFlipFlop {
private:
    bool Q;  // Output
    bool J, K, CLK;

public:
    JKFlipFlop() : Q(false), J(false), K(false), CLK(false) {}

    void setInputs(bool j, bool k, bool clk) {
        J = j;
        K = k;
        CLK = clk;
        process();
    }

    bool getOutput() const {
        return Q;
    }

private:
    void process() {
        if (CLK) {
            if (J && K) {
                Q = !Q;  // Toggle
            } else if (J) {
                Q = true;
            } else if (K) {
                Q = false;
            }
            // Do nothing if both J and K are 0 (no change)
        }
    }
};

class EightBitCounter {
private:
    JKFlipFlop flipFlops[8];

public:
    EightBitCounter() {}

    void clockCycle() {
        // for (int i = 0; i < 8; ++i) {
        //     bool currentBit = flipFlops[i].getOutput();
        //     flipFlops[i].setInputs(!currentBit, currentBit, true);  // J=~currentBit, K=currentBit, CLK=1
        // }
        
        bool done = true;
        
        while (done) {
            for (int i = 0; i < 8; ++i) {
                if (flipFlops[i].getOutput() == 1) {
                    flipFlops[i].setInputs(true,true,true);
                }
                
                else {
                    flipFlops[i].setInputs(true,true,true);
                    done = false;
                    break;
                }
            }
        }
    }

    void displayCounterState() const {
        int counterValue = 0;
        for (int i = 7; i >= 0; --i) {
            counterValue = (counterValue << 1) | flipFlops[i].getOutput();
        }
        std::cout << "Counter Value: " << counterValue << std::endl;
    }
};

int main() {
    EightBitCounter counter;

    // Simulate clock cycles
    for (int i = 0; i < 10; ++i) {
        counter.displayCounterState();
        counter.clockCycle();
    }

    return 0;
}


```


## Question 11 (6 points)
draw a schematic of a hardware controller based on given logic and fundamentals from the lecture notes.

### USB

![](http://csi2372.rambolps.ca:3000/uploads/1ae070b1-06d3-4724-a9ec-ac291a5b1972.png)

### GPIO 

![](http://csi2372.rambolps.ca:3000/uploads/d305924f-1760-4b0c-a3e8-64ffdd83156f.png)


### I2S

![](http://csi2372.rambolps.ca:3000/uploads/fe2c8bf1-b8e8-4b2c-81a9-f68e1a152696.png)


### SPI

![](http://csi2372.rambolps.ca:3000/uploads/0e75bd8a-41b2-495a-93e3-1e108bd4eb9d.png)

### UART 

![](http://csi2372.rambolps.ca:3000/uploads/4395ef0f-cba2-48fa-9a90-60605478871b.png)


