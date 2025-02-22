---
layout: post
title: Schedule Shutdown with PowerAutomate Desktop
category: general
---

![image](https://user-images.githubusercontent.com/58633848/147675926-6f998b59-b9bc-4109-8475-22d28c577402.png)

## Introduction

Today I will show you how to create a PowerAutomate Desktop flow that asks you when you want to shut down your Computer.

The only prerequisites is [PowerAutomate Desktop](https://powerautomate.microsoft.com/en-us/desktop/) and a Microsoft account.

You can also watch the whole walkthrough as video: https://youtu.be/0UEtlwJ8_Es

## 1. Add new flow

Open PowerAutomate Desktop and click on `New Flow`.

![image](https://user-images.githubusercontent.com/58633848/147675586-94088890-977e-4121-aed5-796b2a424905.png)

You can add any name you like. I'm naming mine `Example Shutdown Flow`.

![image](https://user-images.githubusercontent.com/58633848/147676069-9dc55ec0-cc93-4aca-a9f9-e90c25f5bd82.png)

## 2. Select date dialog

Move a `Display select data dialog` to the editor field.

![image](https://user-images.githubusercontent.com/58633848/147676230-6e5322e5-7492-4596-8cf4-0e7a4d227c6c.png)

You can set the `Dialog title` and the `dialog description` as you want. 

Select by `prompt for` `Date and Time`. This is very important.

![image](https://user-images.githubusercontent.com/58633848/147676380-0ee53864-82f0-4e85-8841-0dbc0eb49bea.png)

Now press save and the dialog should close.

## 3. Difference between times

Now we need the difference between the time selected and the current time in seconds.

First add a `Get current date and time` action.

Just click `save` and don't change any values.

Second you have to add a `Subtract dates` action.

In the `From date` field click on the {X} symbol on the right side. Then select `SelectedDate`. 

Do the same thing in the `Substract date` field but ow select `CurrentDateTime`.

Set `Get difference in` to `Seconds`.

![image](https://user-images.githubusercontent.com/58633848/147677099-99c0ed7f-2f23-4d04-9383-af0d34816add.png)

![image](https://user-images.githubusercontent.com/58633848/147677156-39d4262f-90de-48af-ad9e-005e112e4ab2.png)

## 4. Shutdown

Add an `if` element. Set `First operand` to the variable `ButtonPressed`. And `Second operand` to `OK`.

![image](https://user-images.githubusercontent.com/58633848/147677370-046c26a4-aaf4-44ba-aa09-40401c9ce0c5.png)

With this condition the flow only continues when you selected Ok in the dialog. If you click cancel or close Shutdown doesn't get executed.

Add a `Wait` statement into the if statement and set `TimeDifference` as `Duration`.

![image](https://user-images.githubusercontent.com/58633848/147677702-de4169ac-082e-4291-9cd8-8508089ec5ae.png)

Then add a `Shutdown computer` action under the wait statement. Optionally you can select `Force` so that the PC shutdowns also when there are for instance unsaved files.

![image](https://user-images.githubusercontent.com/58633848/147678200-eef39f4a-c947-4b4b-b89f-7e20afcffb9d.png)


## 5. Run 

Now we're finished. Save the flow, close the editor window and then click on run.

![image](https://user-images.githubusercontent.com/58633848/147678303-2a54228e-4d48-4a35-8306-2c056d4a2179.png)

