# OCTANET_FEBRUARY_2
2nd task given by octanet services


<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TODO LIST</title>
 <style>
     * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Times New Roman', Times, serif;

}

body {
    width: 100%;
    min-height: 100vh;
    background: linear-gradient(to top, #021024, #7DA0CA);
    padding: 10px;


}

.todo-app {
    width: 100%;
    min-width: 440px;
    background: #C1E8FF;
    margin: 150px auto 20px;
    padding: 40px 30px 70px;
    border-radius: 50px;
    box-shadow: 0 0 30px;
}

h2 {
    color: #021024;
    display: flex;
    align-items: center;
    font-size: 30px;
    margin-bottom: 50px;
    position: relative;

}

h2 img {
    width: 90px;
    position: absolute;
    right: 0;

}

.row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    outline: 3px groove #021024;
    outline-offset: 5px;
    border: none;
    border-radius: 30px;
    margin-bottom: 20px;
    box-shadow: 0 0 10px #5d5d5d;


}

input {
    flex: 1;
    border: none;
    outline: none;
    background: transparent;
    font-size: 18px;
    font-weight: 600;
    letter-spacing: 1px;
    padding: 10px;


}

input::placeholder {
    color: rgb(2, 2, 34);

}

button {
    border: none;
    outline: none;
    padding: 16px 30px;
    background: rgb(167, 167, 238);
    /* color: ; */
    font-size: 18px;
    font-weight: 600;
    cursor: pointer;
    border-radius: 30px;
    margin: 1px;

}

ul li {
    list-style: none;
    font-size: 18px;
    font-weight: 500;
    letter-spacing: 1px;
    padding: 12px 8px 12px 50px;
    user-select: none;
    cursor: pointer;
    position: relative;
    margin-block: 10px;

}

ul li::before {
    content: '';
    position: absolute;
    height: 30px;
    width: 30px;
    border-radius: 50%;
    background: url(uncheck-16.png);
    /* color: aliceblue; */
    background-size: contain;
    position: center;
    top: 12px;
    left: 8px;


}

ul li.checked {
    background-color: #7DA0CA;
    color: darkblue;
    border-radius: 50px;

}

ul li.checked::before {
    background: url(check-29-16.png);
    background-size: cover;


}

ul li span {
    position: absolute;
    top: 10px;
    right: 0px;
    margin-right: 5px;
    width: 30px;
    height: 30px;
    line-height: 30px;
    font-size: 22px;
    color: black;
    text-align: center;
    border-radius: 50%;
}

ul li span:hover {
    background: black;
    color: beige;
}

ul li.checked span {
    color: white;
}

ul li.checked span:hover {
    background-color: white;
    color: black;
}
 </style>
</head>

<body>
  <div class="todo-app">
    <h2>TO DO LIST <img src="pen_icon1-removebg-preview.png"></h2>
  </div>
  <div class="row">

    <input type="text" id="inputBox" placeholder="Add your task">
    <button onclick="addTask()">Add Task</button>
  </div>
  <ul id="listcontainer">
    <!-- <li class="checked">Task 1</li>
        <li>Task 1</li>
        <li>Task 1</li>
        <li>Task 1</li> -->
  </ul>




  <script>
      let listContainer = document.getElementById('listcontainer');
        let inputBox = document.getElementById('inputBox'); 

        function addTask() {
            if (inputBox.value === '') {
                alert('Add your task');
            } else {
                let task = document.createElement('li');
                task.textContent = inputBox.value;
                listContainer.appendChild(task);

                let span = document.createElement('span');
                span.textContent = '\u00d7';
                task.appendChild(span);
            }
            inputBox.value = '';
            saveData();
        }

        listContainer.addEventListener('click', (el) => {
            if (el.target.tagName === 'LI') { 
                el.target.classList.toggle('checked');
                saveData();
            } else if (el.target.tagName === 'SPAN') { 
                el.target.parentElement.remove();
                saveData();
            }
        });

        function saveData() {
            localStorage.setItem('tasks', listContainer.innerHTML);
        }

        function showData() {
            listContainer.innerHTML = localStorage.getItem('tasks');
        }

        showData();
  </script>
</body>

</html>