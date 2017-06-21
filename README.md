# Bubbling and Capturing

Let’s start with an example.

```html
<div onclick="alert('The handler !')">
  <em>If you click on <code>EM</code>, the handler on <code>DIV</code> runs.</em>
</div>
```
<i>If you click on EM, the handler on DIV runs.</i>

 strange? Why the handler on ```<div>``` runs if the actual click was on ```<em>```?
 
 # Bubbling
 
 Let’s say, we have 3 nested elements FORM > DIV > P with a handler on each of them:
 
 ```html
<form onclick="alert('form')">FORM
  <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
 ```
 
 ![image](https://user-images.githubusercontent.com/6780840/27385283-b4251360-56af-11e7-9650-c89ffd384aa7.png)


So if we click on ```<p>```, then we’ll see 3 alerts: p → div → form.

![image](https://user-images.githubusercontent.com/6780840/27385361-01762f46-56b0-11e7-83e3-1b9b1c82003c.png)

 https://output.jsbin.com/jetupes
 
  Almost all events bubble.
 
 The key word in this phrase is “almost”.
 
 ```
For instance, a focus event does not bubble.
```

<b>The most deeply nested element that caused the event is called a target element, accessible as event.target</b>

* event.target – is the “target” element that initiated the event, it doesn’t change through the bubbling process.
* this – is the “current” element, the one that has a currently running handler on it.
 
 # Stop bubbling
  
  A bubbling event goes from the target element straight up. Normally it goes upwards till ```<html>```, and then to ```document object```, and some events even reach ```window```
  
The method for stop bubbling is ```event.stopPropagation()```.

```html
<body onclick="alert(`the bubbling doesn't reach here`)">
  <button onclick="event.stopPropagation()">Click me</button>
</body>
```

https://output.jsbin.com/guzebow
  
  
  
