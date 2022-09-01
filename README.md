# Exercise-01d-render-get_input-update

Exercise for MSCH-C220

This exercise will get you much closer to a basic solution to Project 01. You will be implementing the game loop using render, get_input, and update functions.

Begin by Forking this repository. Check that it has been forked successfully; the repository should now read [your username]/Exercise-01d-render-get_input-update

Edit the LICENSE and replace BL-MSCH-C220-F22 with your full name. Commit your changes.

Press the green "Code" button and select "Open in GitHub Desktop". Allow the browser to open (or install) GitHub Desktop. Once GitHub Desktop has loaded, you should see a window labeled "Clone a Repository" asking you for a Local Path on your computer where the project should be copied. Choose a location. Make sure the Local Path ends with "Exercise-01d-render-get_input-update" and then press the "Clone" button. GitHub Desktop will now download a copy of the repository to the location you indicated.

The first step will be to export Zork.html as a json object. If you have not installed the "JTwine-to-JSON" format, do that first: (In the Twine menu at the top of the window, select "Story Format". You should see a list of possible story formats for Twine. In the top left corner is a button labeled "+ Add". Select that now. The resulting pop-up window should read "To add a story format, enter its address below." Enter `https://cdn.githubraw.com/BL-MSCH-C220-F22/JTwine-to-JSON/main/format.js` and press the green "+ Add" button.)

Next, in the Library menu, select the Import button. In the resulting popup, navigate to the exercise folder on your computer and select Zork.html. Select the "Zork" story, and then press "Import Selected Files". After it has loaded, In the Story menu at the top of the window, select Details. You should now see a pop-up in the bottom-right corner. Change the "Story Format" and select "JTwine-To-JSON 0.1.0". Now press Build->"Play"; a browser window should open with the Zork story represented as a JSON object. 

Create a new python replit project; name it Exercise-01d-render-get_input-update. In the resulting main.py, paste the following:
```
zork = {}

# ----------------------------------------------------------------

def find_current_location(world, pid):
  if "passages" in world:
    for passage in world["passages"]:
      if pid == passage["pid"]:
        return passage
  return {}

# ----------------------------------------------------------------

def render(world, current_location):
  pass

def get_input():
  return "QUIT"

def update(world, current_location, current_pid, response):
  return current_pid

# ----------------------------------------------------------------

pid = 0
if "startnode" in zork:
  pid = zork["startnode"]
current_location = {}
response = ""

while True:
  if response.upper().strip() == "QUIT":
    break
  pid = update(zork, current_location, pid, response)
  current_location = find_current_location(zork, pid)
  render(zork, current_location)
  response = get_input()
print("Thanks for playing!")
```

Now, replace the {} (on line 1) with the JSON object you exported out of Twine.

Your final task is to implement each of the three functions that are part of the game loop: render(), get_input(), and update().

render() should display the name and description (using the "cleanText" key) of the current location. You can choose to print out the player's options if you would like to.

get_input() should ask the player what they would like to do and return what the player types in response. If should correspond with the "selection" field in the "links" list inside current_location.

update() should check the player's response against the list of links in the current passage. If the player's response matches the selection, update() should return the pid of the new location.

This is probably the biggest learning-curve jump so far, so if this seems overwhelming, feel free to follow my video demonstration. When you are done, run the program to make sure it is functioning correctly.

In your replit project, create a new README.md file and paste in the following contents (replacing my information with yours). When you have finished editing, commit your changes, and then turn in the URL of your replit project (https://replit.com/@[username]/Exercise-01d-render-get_input-update) on Canvas.

The final state of the README.md file should be as follows (replacing my information with yours):
```
# Exercise-01d-render-get_input-update

Exercise for MSCH-C220

A simple interactive-fiction game loop that allows players to experience eight locations from the classic Zork, implemented in Python.

## Implementation
Created using Python 3.8

## References
[Zork, 1977 by Tim Anderson, Marc Blank, Dave Lebling, and Bruce Daniels](https://en.wikipedia.org/wiki/Zork)

## Future Development
None

## Created by
Jason Francis
```
