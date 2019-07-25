# Unit 1 Review Lab

Before completing any of the review questions below, ensure that you have answered each question in the previous labs.

## Question 1 - done

Given the following excerpt from the Declaration of Independence, find the most frequent word that is longer than 5 characters.

 - use components(separatedBy:) to break up the string into an array.
 - use CharacterSet.punctuationCharacters in union with any other characters you don't want in your array, like spaces and new lines.

```swift
let declarationOfIndependence =

"""
When in the Course of human events, it becomes necessary for one people to dissolve the
political bands which have connected them with another, and to assume among the powers of the
earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle
them, a decent respect to the opinions of mankind requires that they should declare the causes
which impel them to the separation.
We hold these truths to be self-evident, that all men are created equal, that they are endowed by
their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit
of Happiness. That to secure these rights, Governments are instituted among Men, deriving
their just powers from the consent of the governed, That whenever any Form of Government
becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to
institute new Government, laying its foundation on such principles and organizing its powers in
such form, as to them shall seem most likely to effect their Safety and Happiness. Prudence,
indeed, will dictate that Governments long established should not be changed for light and
transient causes; and accordingly all experience hath shewn, that mankind are more disposed to
suffer, while evils are sufferable, than to right themselves by abolishing the forms to which they
are accustomed. But when a long train of abuses and usurpations, pursuing invariably the same
Object evinces a design to reduce them under absolute Despotism, it is their right, it is their duty,
to throw off such Government, and to provide new Guards for their future security. Such has
been the patient sufferance of these Colonies; and such is now the necessity which constrains
them to alter their former Systems of Government. The history of the present King of Great
Britain is a history of repeated injuries and usurpations, all having in direct object the
establishment of an absolute Tyranny over these States. To prove this, let Facts be submitted to a
candid world.
"""
var noPunct = ""
for i in declarationOfIndependence {
if i != "." && i != "," && i != ";" {
noPunct.append(i)
}
}

var newArray = noPunct.components(separatedBy: " ")

print(newArray)
```

## Question 2 - done

Make an array that contains all elements that appear more than twice in someRepeatsAgain.


```swift
var someRepeatsAgain = [25,11,30,31,50,28,4,37,13,20,24,38,28,14,44,33,7,43,39,35,36,42,1,40,7,14,23,46,21,39,11,42,12,38,41,48,20,23,29,24,50,41,38,23,11,30,50,13,13,16,10,8,3,43,10,20,28,39,24,36,21,13,40,25,37,39,31,4,46,20,38,2,7,11,11,41,45,9,49,31,38,23,41,16,49,29,14,6,6,11,5,39,13,17,43,1,1,15,25]

let duplicates = Array(Set(someRepeatsAgain.filter({ (i) in someRepeatsAgain.filter({ $0 == i }).count > 2})))

print(duplicates)
```

## Question 3 - done

Identify if there are 3 integers in the following array that sum to 10. If so, print them. If there are multiple triplets, print all possible triplets.

```swift
var tripleSumArr = [-20,-14, -8,-5,-3,-2,1,2,3,4,9,15,20,30]


func findTriplets(arr: [Int],sum: Int) -> [[Int]]{
var triplets: [[Int]] = []
for i in arr {
for j in arr{
for k in arr {
if j + k + i == sum {
triplets.append([j,k,i])
}
}

}

}
return(triplets)
}
print(findTriplets(arr: tripleSumArr, sum: 10))

//if there is a way to do this with closures i would love to know

```


## Question 3...again? - done

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a. Sort the string below in descending order according the dictionary letterValues
var codeString = "aldfjaekwjnfaekjnf"
```
var codeArr: [Int] = []

for i in codeString {
let strI = String(i)
codeArr.append(letterValues[strI] ?? 0)
}
let sorted = codeArr.sorted { (int1, int2) -> Bool in
return int1 > int2
}
var newStr = ""

var reversedDict = [Int: String]()

for (k,v) in letterValues {
reversedDict[v] = k
}

for i in sorted {
newStr.append(reversedDict[i]!)
}
print(newStr)
```


b. Sort the string below in ascending order according the dictionary letterValues
var codeStringTwo = "znwemnrfewpiqn"
```var codeArr: [Int] = []

for i in codeString {
let strI = String(i)
codeArr.append(letterValues[strI] ?? 0)
}
print(codeArr)
//
let sorted = codeArr.sorted{ (int1, int2) -> Bool in
return int1 < int2

}

print(sorted)
var newStr = ""

var reversedDict = [Int: String]()

for (k,v) in letterValues {
reversedDict[v] = k
}

for i in sorted {
newStr.append(reversedDict[i]!)
}

print(newStr)
```


## Question 4 - todo

Given an Array of Arrays of Ints, write a function that returns the Array of Ints with the largest sum:


```swift
Input: [[2,4,1],[3,0],[9,3]]

Output: [9,3]
```

## Question 5 - done

```swift
struct Receipt {
let storeName: String
let items: [ReceiptItem]

func totalCost() -> Double{
var price = [Double]()
for item in items {
price.append(item.price)
}
return price.reduce(0,+)
}
}

struct ReceiptItem {
let name: String
let price: Double
}


```

a. Given the structs above, add a method to `Receipt` that returns the total cost of all items

b. Write a function that takes in an array of `Receipts` and returns an array of `Receipts` that match a given store name

```func sameNames(reciept: [Receipt], storename: String) -> [Receipt] {
let returnArray = reciept.filter { ($0.storeName == storename)
}
return returnArray
}

```

c. Write a function that takes in an array of `Receipts` and returns an array of those receipts sorted by price
```
func sortedByPrice( ticket: [Receipt]) -> [Receipt]{
let sortedPrice = ticket.sorted { (ticket1, ticket2) -> Bool in
return ticket1.totalCost() < ticket2.totalCost()
}
return sortedPrice
}
```

## Question 6 - done

a. The code below doesn't compile.  Why?  Fix it so that it does compile.

```swift
class Giant {
    var name: String
    var weight: Double
    var homePlanet: String
    
//changed constant homePlanet into mutable variable

    init(name: String, weight: Double, homePlanet: String) {
        self.name = name
        self.weight = weight
        self.homePlanet = homePlanet
    }
}

let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")

fred.name = "Brick"
fred.weight = 999.2
fred.homePlanet = "Mars"
```

b. Using the Giant class. What will the value of `edgar.name` be after the code below runs? How about `jason.name`? Explain why.

```swift
let edgar = Giant(name: "Edgar", weight: 520.0, homePlanet: "Earth")
let jason = edgar
jason.name = "Jason"
//because jason is an instance type of edgar and Giant is a class which is a reference type when jason.name is changed so is edgar.name
```


## Question 7 - done

```
struct BankAccount {
var owner: String
var balance: Double
var deposit: Double
var withdraw: Double
private var startingBalance: Double{
get {
return balance
}
}

mutating func deposit(_ amount: Double) {
balance += amount
}

mutating func withdraw(_ amount: Double) {
balance -= amount
}

mutating func totalGrowth() -> Double {
return startingBalance + deposit
}
}


//code didnt compile because methods were not mutating functions
```
 
a. Explain why the code above doesn't compile, then fix it.

b. Add a property called `deposits` of type `[Double]` that stores all of the deposits made to the bank account

c. Add a property called `withdraws` of type `[Double]` that stores all of the withdraws made to the bank account

d. Add a property called `startingBalance`.  Have this property be set to the original balance, and don't allow anyone to change it



e(TODO). Add a method called `totalGrowth` that returns a double representing the change in the balance from the starting balance to the current balance

## Question 8 - done

```swift
enum GameOfThronesHouse: String {
case stark
case lannister
case targaryen
case baratheon

func printString(house: GameOfThronesHouse) {
switch house {
case GameOfThronesHouse.stark:
print("Winter is coming")
case GameOfThronesHouse.baratheon:
print("Ours is the Fury")
case GameOfThronesHouse.lannister:
print("A Lannister always pays his debts")
case GameOfThronesHouse.targaryen:
print("Fire and Blood")
default:
" "
}
}
}

```

a. Write a function that takes an instance of GameOfThronesHouse as input and, using a switch statement, returns the correct house words. - DONE

```
House Baratheon - Ours is the Fury

House Stark - Winter is coming

House Targaryen - Fire and Blood

House Lannister - A Lannister always pays his debts
```

b. Move that function to inside the enum as a method - DONE

## Question 9- done

What are the contents of `library1` and `library2`? Explain why.

```swift
class MusicLibrary {
    var tracks: [String]

    init() {
        tracks = []
    }

    func add(track: String) {
        tracks.append(track)
    }
}

let library1 = MusicLibrary()
library1.add(track: "Michelle")
library1.add(track: "Voodoo Child")
let library2 = library
library2.add(track: "Come As You Are")

//the songs added to tracks property "Michelle","Voodoo Child", "Come As You Are" are both in library1 and library 2, because library is an instance of MusicLibrary which is a reference type any changes to library1 will also change its instances.
```

## Question 10

Make a function that takes in an array of strings and returns an array of strings. The function should determine if the string can be typed out using just one row on the keyboard. If the string can be typed out using just one row, that string should be in the returned array.  

```


Output: ["Alaska", "Dad", "Power"]
```
