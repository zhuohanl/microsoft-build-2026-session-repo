**Microsoft Build\
June 2-3, 2026\
Session: BRK241\
Speakers: Jeff Hollan, Tina Schuchman**

**Tina Schuchman:** Hi, everyone. My name is Tina Schuchman, Corporate Vice President on Microsoft Foundry. Along with me is Jeff Hollan, Partner Director on our Foundry Agent platform.

We're super-excited to be with you today. For the next 45 minutes we're going to walk you through building an agent locally, host it in a sandbox, have it run production workload, and operate it to see it self-improve. So get excited. Before we get started, I would love to ground us on where we are today. We have entered a new era of AI agents. Three things are true. One, building is no longer the hard part. With coding agents, such as GitHub Copilot, GitHub Copilot CLI, and Claude Code, any developer is able to stand up a powerful agent within minutes. The question has shifted from, "Can I build it," to, "Can I run it reliably at enterprise scale?" Two, agents' capabilities have exploded. We're no longer building agents that are static routers shuffling requests between a fixed set of tools. Today's agents can spawn off new agents that have full access to their compute environments. They can create new skills, they can generate new memory. They can get things done that they were never programmed to do to start with. They are general purpose systems. And the third shift, which may be the biggest shift of all, agents are teammates, not tools.

We're no longer building chatbots. We're building agents that take on significant business outcomes. They do whatever is needed to get that outcome done by chatting not only with people but also with other agents. Now let's put that in the context of your entire business

across every single function compliance finance supply chain support businesses that

one don't just build one super-powerful agent they have AI at the core of every single function. They have a coordinated system of agents that are all carrying out business-critical tasks. They have all of these agents that are long-running and they are having -- they are carrying out high-value actions so your team of agents become a team of operators continuously learning

continuously improving. So that demands not just a build platform, it demands an entire operating system for your enterprise AI transformation. And that is what Foundry gives you. And that's where our systems advantage comes in.

Microsoft offers the most complete system for any enterprise, Foundry, Azure, GitHub, Microsoft 365, Microsoft Security, all working as a holistic system, not siloed tools. One use that we have is that AI systems are never done. They run on production-learning loops. So you may build your agent in GitHub with GitHub CLI.

You could find the emails that tell us what good looks like. You then deploy it right into Foundry, so it runs on production workloads. Every single action, every single cost signal is then set into the evaluation and optimization service, which then continuously learns, continuously improves. The system compounds the more it runs. So it's no longer about fine-tuning a specific model it is about improving this entire system through tuning your models

tuning your harness your contacts your memory all with developer in control for every single change. So your enterprise can continue evolving its production agents rather than having to rebuild from scratch every single time. This is how you transform your enterprise with agents. Now let's talk about our demo scenario.

Microsoft runs the world's largest cloud infrastructure. Sometimes bad things happen, such as a fiber cable gets cut near one of our data centers. When that happens today, we need an agentic system that is able to respond, dispatch, resolve really fast. Today we have our Azure Networking Operations team who has built such an agentic system that are not only coordinating with humans, but also other agentic systems to resolve incidents like this. We're going to build one such agent today, autonomous cyber outage response agent.

I know it's a handful, but. So the sensor detects the fiber outage, and then it sends a signal to trigger the agent. The agent wakes up and it looks up all the important information in Foundry Toolbox, and looks up the worksite reliability information as well as the location information in Fabric IQ. It looks up the supplier conversations information in Work IQ. It looks up all the specific work orders as well as supplier agreement information in RALA documents through our Document Intelligence and Content Understanding service.

It then dispatches a field rep to go respond to the incident, it files a ticket to be tracked in D365, and then it publishes the latest status right into Teams so everyone is aware of what's going on. So we're going to show you the demo through three developer phases, build, deploy, and operate, all in a continuous learning and continuous improvement loop. So that is the what and the why. Let us now show you the how.

Jeff, let's show what a develop can do.

**Jeff Hollan:** Great, awesome.

Thanks so much, Tina. And as she mentioned, we actually want to spend the majority of today showing you this in action. As much as everybody loves looking at slides created by our amazing Marketing team, we're going to spend the majority of the session actually building this live. So let's go ahead and talk about some of the problems that we're going to surface on here on the next slide in this build phase, the part of the phase that has to do with actually creating these agents.

Because as a developer, I have a bunch of pieces in the next slide -- oh, we're showing my screen, that's fine. I'll talk to this screen for a second. I'll just tell you the challenges.

Don't worry, visualize this slide in your mind, our Marketing team made a great one. There's a few challenges on the build phase. It's like, "How do I choose the right framework?

How do I choose the right model? How do I make sure that my agent has access to the right context?" Think of all the knowledge and information in your organization that is helping your agent be powered how do you get all of that integrated secured with the right identity

and ready to run even in natural interfaces? Sometimes that might be through chat experiences, other times that might be through voice.

Now part of what I want you to pay attention to as we go through building this today is while many of these pieces exist in the ecosystem what we really want to provide for you here in Foundry is a single platform that brings it all together. So I'm not going to have to jump between a whole bunch of different tools and platforms to do what we've described in making sure that we are repairing our fiberoptics lines if something was to ever happen at one of our regional centers.

So let's get started. You can see here I just have a blank canvas. You can use any tool that you want when working with Foundry, whether you like Claude Code, GitHub Copilot CLI, Cursor, Visual Studio. My personal favorite combo is Visual Studio Code with GitHub Copilot. Now, one of the reasons that I like it is because we have this Foundry Toolkit extension. This is now generally available. You can see this actually gives me a bunch of pieces that I need for this entire flow. It's not just about creating agents.

You can see I have information here about tracing and evaluations, making sure I have the right models. All of this is right here integrated for me. Now, if I want to go ahead and create a new agent, I have a few different options. I could use one of our samples if I'm just trying to get a feel for what's possible, or my personal preference is to generate with Copilot. Now, we can help give you an idea right here, but let's go ahead and build the scenario that's closer to what we want, which is, "Hey, help me create an agent that can act with our Field Operations team. When somebody goes on site to try to repair one of these fiberoptic lines

I want to make sure that they have the right information whether it's from Work IQ or Fabric IQ or Foundry IQ to actually go do this." Now let's go ahead and not install a new model.

No. But they'll still go ahead and work behind the scenes. One of the things that I love about this extension, which we're just going to let this play nicely.

Sure, just download it. If it's going to make you happy, let's go ahead and download this. Okay, so one of the things that I love about this extension -- this is how you know, by the way, this is as live as it gets, is that this actually integrates with it best practices automatically from Foundry. So this includes -- if I get rid of all of these popups, oh my goodness, this AI agent expert. This has baked in a bunch of skills out of the box, based on Foundry best practices. So you can install these skills standalone into your coding agent, but this extension will actually integrate them automatically with my workload so that as it's generating the agent, it's able to do so with the right best practices. Okay, let's go back here. Get this desktop out of the way. Let's jump ahead, "Hey, Copilot, you generated this amazing agent." It pulled it out of the oven a little bit.

That's fine. All right, a few things here I want to call out. Like I said, Foundry you can use any framework that you want. I'm personally here using Microsoft's Agent Framework inside of Python. Now, Agent Framework is phenomenal at doing things like multi-step or multi-agent workflows. One of the new capabilities that we're actually leveraging in this is the new harness inside of Agent Framework.

This gives a secure environment for your agent to be able to do things like execute shell commands, read, write, and execute code, all with a harness that's operating and managing with it. I can even plug in the GitHub Copilot SDK as an additional harness as I want. Now, this makes these agents much more capable. Agents today are no longer just about executing the predefined tools that you've configured, it can actually dynamically do investigations, code writing, and code authoring along the way.

You're going to see that as we go throughout the rest of this demo. Now, one critical piece of any agent is having access to the right tools. So I'm going to show you here right inside of Visual Studio Code how I can go ahead and start to add and integrate with various tools. Now, if there's one feature that I want you to remember when it comes to tools, it is Foundry Toolbox. Now, I can actually manage this right here in Visual Studio Code.

This gives me a bunch of stuff automatically. First, I can configure for this agent or a collection of agents a set of tools that I want to configure for my task to be done. Now, what Toolbox is going to do is it gives me a single spot to manage them all. It's handling authentication between things like Foundry IQ, where I have different documents that I've indexed around like our supplier contracts or our supplier agreements. It integrates with things like Web IQ and web search. You can see here I've integrated Fabric IQ. I have a bunch of site reliability data

"Hey how are my sites in terms of uptime and reliability?" that's all surfaced through Fabric which I'm using Fabric IQ to integrate with and I also want to make sure I have a history and access to integrate with things like tools from Teams and Outlook so I'm able to add Work IQ here. Toolbox gives me this one spot it's going to manage the authentication.

I can set guardrails as well. So if I want to make sure that I'm specifying and making sure that personally identifiable information doesn't leak from any of these tools, I can configure that right away. I love this specific feature of Toolbox, which is called "Tool Search". If you think about all of the context required for my agent to reason around all of these tools, not all of them might be relevant.

So if I turn on "Tool Search," whenever I talk to Toolbox through this single MCP compatible endpoint, it will only return back the tools that are relevant for that specific task. Now, this allows me to really optimize my context utilization and my context window, so I can keep my agent focused on its most immediate needs. Now, one more thing I'll just slip in here very quickly, I could add additional tools.

We have thousands of them. One of the cool ones here is actually Content Understanding. There's a session later tomorrow on Content Understanding I'd recommend you check out. But what Content Understanding lets me do is like I have a document here. This is actually a PDF document. You can see it's a PDF but it has tabular data, it's not very agent-readable, not without additional analysis. What Content Understanding will do is it will use a specialized model to turn a PDF of a document a contract a specification

you name it and it will actually convert it into an agent and AI ready format so I can pull out the tables the markdown

the figures or even get the raw JSON. So that's what I've connected my agent to do. So now I have this fiber-operations agent.

I've got everything that I need here. I've connected the right tools. The other thing that I love about working right here inside of Visual Studio Code is I can do this magical gesture. When we think about Satya's keynote today and we're showing how cool it is that now you can have UI and Code working together, well in Foundry I can F5 debug my agent. So it's actually spinning up my agent locally. It's going to connect to Toolbox. In fact, I can show you how simple the line is to integrate with Toolbox. It's a single MCP-compatible endpoint that I can integrate with, and this is now spun up for me on my local host, my agent, that I can start to interact with. So let's go ahead and ask this a question. Let's say, "Hey, I'm on site. I'm trying to figure out why there's some downtime. Can you help me understand why this -- or what is the right connection type that I should use?" Now, you'll notice ahead of time I actually set a breakpoint.

My breakpoint was hid. If I wanted to inspect a little bit more of the request or the response, I have all of the tools and debugging that I would need to make sure the agent is behaving how I want to. And right here, all inside of Visual Studio Code -- this has been my home the entire time, I can see the different events that are streaming in and out of the agent and how it's working to answer this question. So this gives me this building flow pulling in the right tools from the right context whether it's Web or Foundry

or Fabric or the Microsoft Graph with Work IQ connecting them with a framework that has a harness to actually go and understand things like the specification that it needs to look up. There's one more thing I want to show here, which is that while this is useful if I was deploying this as a chat application that maybe I want one of these contractors to use when they're repairing the site, they're also on the job. Right, when I'm asking a question about the Quincy North site connection type, I'm probably wearing something like work gloves, my hands are probably occupied.

Using a chat interface with gloves, leather gloves, is not a good experience. Okay, so I want to now voice-enable this agent. And in Foundry we want to make that very easy as well. I can go ahead and choose now to deploy this agent into Foundry. So this will take all of the code that I've run here and deploy it into my Foundry account. And what I can do here now is I'm going to switch to a version I deployed ahead. This is my favorite part of this demo, how easy is it to make your agent voice-enabled, watch this.

Here's the magic. Voice mode, done, okay? We will automatically wrap industry-leading voice models. I can configure them over here if I want to specialize them, choose the right voice model. But this is now taking what was built as a Microsoft Agent Framework agent and I put this voice interface on it. So now this is the real moment of truth, I'm going to go ahead and unmute my speakers and we're going to try to talk to our agent friend here through voice. Let's give it a shot.

Hey, can you pull up the fiber termination spec for the Quincy North site and tell me which connector I should use on the B side panel? Let's hope that the volume --

**Speaker 1:** Just a sec.

**Jeff Hollan:** Okay, great. So you can hear it's starting to answer back. It even has -- as the responses are streaming back in real time, this has opened a web socket with that voice connection. So it's now able to --

**Speaker 1:** Welcome. Pulling that up now.

**Jeff Hollan:** Thank you for pulling that up now. So it's reaching into those tools, right, it's iterating through Toolbox and giving me little updates. This might --

**Speaker 1:** Getting the spec now.

**Jeff Hollan:** This might not happen instantly, right, with agents like Claude Code or Copilot SDK.

**Speaker 1:** Pulling up the spec now. Here are the fiber termination specifications for the Quincy North site's B side panel. Connector family, LC UPC Duplex required on B side panel.

**Jeff Hollan:** Great. That's pretty cool, right? Not bad that I was able to turn this agent into a voice-optimized agent in no time at all. All right, so I'm going to bring Tina back on to take us into the next chapter of how we're going to take this agent that I just developed quickly in Visual Studio Code and deploy it at scale with Foundry.

**Tina Schuchman:** Thank you, Jeff.

That was fantastic. Let's take a look at the features that Jeff just showed us. Okay. First is Microsoft Agent Framework, now in Version 1.0, production ready. As Jeff mentioned, Microsoft Agent Framework now has a built-in harness that's well-integrated with skills, memory, middleware. It also has plugins integrations with harnesses such as GitHub Copilot SDK and Claude Agent SDK. Foundry Toolkit for VS Code is now generally available. Foundry Toolkit provides a purpose-built developer experience for building Foundry agents without you having to ever leave the editor. Toolboxes in Foundry is generally available soon. Toolboxes provides one single manage endpoint for all the tools that are making your agents powerful, all with the right governance and policy in place.

Skills are now a first-class integration with Toolboxes as well. Voice Live integration with Foundry Agent Service is generally available today for prompt agents in public preview for hosted agents to support our speech and voice scenarios. I'm super-excited to announce that hosted agents in Foundry Agent Service is generally available soon. Per session sandbox isolation, sub-second code start, zero idle time cost, framework agnostic, that's Foundry hosted agents.

Now even supports long-running autonomous agents such as OpenClaw and Hermes agents, all with durable safe execution and file system access. Super-excited. And now that we have a local agent we scaffolded on a laptop, how do we now get it into production, Jeff?

**Jeff Hollan:** All right, let's check it out. So if we want to think of the next set of challenges that we have that Tina addressed if I think of the agents today that are really transforming even how I work these are not just reactive-based agents that I go to with a question in a chat window and they come back to me with an answer. These are agents that I need to be long-running, that are maintaining and building context over time, accomplishing tasks that might take days or even weeks.

Now, I need to be able to do that in a secure way. If we think about these types of agents that I mentioned that have this agent harness, these might be reading and writing code. I want to make sure that I'm isolating these instances from each other.

Now, I want to make sure that I'm getting these also in front of users through the interfaces that they care about. I don't want to make everybody add 10 new bookmarks to their browser to remember the 10 cool agents that the team is building. And each one of these agents starts to become a lot more like a teammate, somebody who is helping alongside, being proactive, giving me suggestions as I go. So we want to bring those same capabilities into this agent that we started here. So I'm going to show now on my laptop a different flavor of our agent friend, and this is my agent called "Fibey".

Now, Fibey is a claw-like agent. Fibey is monitoring our telemetry and our uptime for our networking over time. And I'm going to show you some of the capabilities in Foundry that allow me to build these clawlike agents right here.

And we'll talk about more, and there's a whole session that goes into this tomorrow morning, so you can go in. One of the coolest pieces here is this new feature in Foundry called "Routines". This is really what makes my agents become proactive instead of reactive. I can set up different events that can actually proactively wake my agent on different tasks.

So you can see here I configured a simple heartbeat. We'll go ahead and open this up. So I've told this thing, "Hey, every hour I want you to wake up and I need you to do a few things. I want you to check the investigation log.

I want you to see if there are any anomalies. If there are any anomalies, I need you to follow the different skills that you have to make sure that you're alerting the right person, that you're issuing the right subcontractor." The Azure Networking team actually does this in real life. When an incident happens that affects some of our networking, an agent can automatically interact, wait for human approval as necessary, and start to get somebody on site to go repair the site. So this heartbeat, this routine is part of what enables this thing to be proactive because it's going to check for these anomalies on its own. So you can see that over the last bit, this has actually been firing off a number of these different routines. Now, one piece that's critical here for these long-running agents is around security. So of course, if you're thinking about claw-like agents, you probably have in your mind like a dedicated Windows machine or maybe a dedicated Mac mini. The reason that folks do that is you want to make sure this agent works in its workspace, that it's doing so in a secure way. Imagine that I have subcontractor A and subcontractor B and they're both interacting with Fibey in different ways. Well, what if Fibey is reading and writing files that has subcontractor A specific or sensitive data in it and it's actually saving those files locally? Well, what if that same process, that same agent, subcontractor B's agent, gets a little bit creative and it goes and pull some of those files, right, you can start to leak context, you can start to leak code execution, it becomes a nightmare.

We want to make that easy for everyone to solve. So this new hosted agent capability that Tina mentioned becomes generally available soon, the way that this works is every single conversation, every single routine, if I want, can kick off its own dedicated session. So you can see here I have a number of sessions that have kicked off.

Each one of these is its own isolated workspace. So everything the agent does happens separate from every other conversation, but I still have durable persistence state. So for instance, I can open this one that's been idle since 11:00 a.m.

this morning, it looks like. I can see the logs of this routine and I can actually inspect what was the state of the file system when this went idle. So as this loads up, you can see this actually saved a number of files to its file system.

You can see it had some anomaly analysis, some vendor context, some investigation. This is all breadcrumbs that the agent is able to write just like a claw-like agent on my machine, but it's now doing so securely in the cloud. Now, I mentioned this is idle, which is awesome because this is waiting for an approval or maybe it didn't find any event right now.

I'm not paying any money when this is idle. But what happens when it needs to wake up again? Well, when it wakes up, we will resume the session, we'll take all of the state of that session, all of those investigation files, we will give it back to the agent to continue its work. In fact, I've extended these out-of-the-box sessions with the Durable Task Scheduler. This allows me to monitor the state even when all of my sessions are idle.

So let me give you an example. Let's say Fibey wakes up, it finds something, and it needs to wait for human approval. This has been sitting here for I think two or three hours at this point, waiting for me to click "Approve". All of my sessions are idle. But right now Durable Task is saying

"Hey you have this instance that is sitting here waiting for approval." Now this is all serverlessly running so again

my session's not running but Durable Task has some additional state that I integrated using the Microsoft Agent Framework extension for Durable Task. Now watch what happens. I'm going to go ahead and click "Approve". When I click "Approve," a few things are going to happen all at once. I'll go ahead and refresh this view in Durable Task. You can see I have this long wait period where it was waiting. Well, now Durable Task said, "Oh, I got my approval, go resume the session." So now it comes over here. And let's do another refresh.

Let's refresh over here on the Foundry Session view, and we will see hey, this woke back up that session, my session resumed, and it had all of the investigation files from before, and it went ahead and continued the work. So I have this long-running secure way to manage agents at scale where I can do these things like human intervention without worrying about rehydrating and restarting the state every single time. Now the last piece here that I want to show -- and you might have seen this a bit in the keynote this morning any of these agents that I build I can make easily available to my entire team not just setting up routines or through custom maps like that Fibey portal that you saw

I can publish these easily to Teams and Microsoft 365 Copilot. So if I go ahead and choose this option, this will walk me through all the steps that I need to deploy it. Now you can see this is actually already deployed, so I'll go ahead and switch over here. This is actually working as an autonomous agent right now in Teams.

It has its own identity. It even has its own email address. You can see fibey@notareal.co.

I'm pretty sure it's a real company, though, don't worry about it. And I can come in here and go ahead and ask Fibey a question and I'm saying like "Hey Fibey what are some of the active incidents that you're working on right now?" That same agent that I was showing you before running inside of Foundry it's now either resumed my session or started a new one and you can see Fibey is now doing the work required to come back and give me an update on my status.

So I have this possibility to build the claw-like agents, integrate them into services like Teams, with all of the critical building blocks that I need, all within Foundry. So with that, Tina, back to you for our next chapter.

**Tina Schuchman:** Thank you, Jeff. Now let's take a look at the features Jeff just showed. Number one, Routines, now in Foundry Agent Service in public preview. Routines is what makes your agent from reactive to proactive and makes it long-running.

You as the developer decide what needs to happen when. Foundry then cues, executes, and tracks every single run. This is how you turn your reactive one off task into a proactive continuous agent. Published to Microsoft 365 Teams and Copilot is generally available soon. Now, you can publish all your Foundry agents right into Teams and Copilot where all your teams are already doing work. Identity, policy, permissions all flow through automatically. In addition, developers now can publish Foundry agents as autopilot agents right into Teams.

This is now in public preview. So these autopilot agents can take on functional IDs email addresses and even Teams' presence so they can start -- initiate -- they can initiate a conversation or follow up on action items all governed end-to-end in Agent 365. So now we have built an agent locally, we have hosted in a sandbox, we have published as an autopilot agent right inside of Teams. Now let's enter the hard part, which is operate.

How do we make sure the agent runs well and it can self-improve? Jeff?

**Jeff Hollan:** Okay, I'm ready. All right, this is the last, and if I might say, maybe the best chapter of it all.

I'm a little under the weather. I'm going to hope my voice hold out for another 10 minutes, but I'm feeding off of your energy. Okay, so let's take a look about some of the challenges that come on this optimization phase as well, right? Here, this is really where the work begins. I can go build and prototype really cool agents in a number of hours or days, but how do I actually go make this thing trusted in production? How do I make sure I'm understanding how are people using my agent, what are the signals that are happening, what's being successful or what's not successful, how do I understand where I need to improve it?

Now this is also very challenging because if you think of all of the components involved with like the agents that we've been building I've got the underlying model

I have my toolbox and all the tools that are there I've got my own code I've got the instructions in my code. If I'm having an issue with my agent, which one of those variables should I tune and tweak?

It can become very overwhelming and very time-consuming. So I want to show you how Foundry is helping you in this last mile to really make these things robust. Now, the first piece here is visibility.

I want to understand what is happening and why it's happening. So in our Fibey agent right here, I can come over here to see all of the conversations that are happening across this agent. But one of my favorite features here is I can click any of these -- let's just go ahead and try this request right here, and we have this new view that is rolled out, which is called the "Trace Replay" view. So check this out, I see the conversation that has happened. I can understand from a basic thing what was the question that was asked and what was the answer. But I can understand the trajectory that this specific request took. So I can understand, "Okay, I got asked this agent. It first had to do some reasoning on this model.

That took about 20 seconds. It then called this tool, then it reasoned, then it called this tool." Any of these I can click in to understand the exact inputs and outputs that went along the way. If I'm feeling extra fancy, I can not only just see this from a time perspective, but a token perspective.

Where are my tokens being consumed throughout the process of this request? And if I want to get especially fancy, check this out, I'm actually going to replay this. Let's do this at eight times the speed. And let's actually watch as this plays through the entire conversation so I can understand each of the phases that went through what the agent was doing and get a view into what the users saw throughout this process. So I'm able to dive deeper to understand the specifics of what's happening and get that observability view right at my fingertips. Now, let's say that I see something that I want to improve.

For our agent I'll tell you a real piece of feedback that we saw as we were building this which was if you remember back to that demo we did with the voice-enabled agent at the beginning right where I said

"Hey give me that specification." I'm showing you the answer now. How the agent is answering is a very LLM way of doing things. It actually returned a bullet point list. It said, "Hey, you want to know the connection? Here's the bullet point list of all that stuff." But some of you might have been listening in that first demo and you're like

"Wow this sounds a little bit robotic." as the voice just reads through a bullet point list of topics. So I actually want to optimize my agent. I want to make it so that it's returning a more voice-natural response. But how do I go about doing that?

Which of all these things should I be tuning or adjusting? So let's actually walk through that process here. I'm actually going to jump over here to my terminal, which is my best friend in the world.

Let's zoom in here really, really, really tight. And I'm going to kick this off with the first command, which is azd, which is the Azure Developer CLI AI agent eval init. Now, this will take our agent project and it's going to initialize it and get it ready to run evaluations so that I have a benchmark evaluation that I can improve this thing against. Now, the voice-enabled agent was this field operation spacing agent, so we'll go ahead and choose this one. And this is going to do a few things for me.

Now I've generated these ahead of time but the first thing it's going to do is

"Hey do you already have an eval dataset?" Now many of you love to talk about evals but you don't actually have an eval dataset.

And that's okay, I'm not going to judge you, I'm often in the same boat. Here you can actually ask us to help you generate an eval dataset automatically. How that works is we'll go look through all of those historic traces additional signals that we have about your agent and we will go ahead and suggest using an LLM

an initial starting point dataset based on how your agent is actually being interacted with. So this can help you actually practice what you preach if you are in that camp of talking about evals but not having them. Now, the other piece here is how do I have the right evaluation logic, though? How do I have the right evaluator? Now, what do I mean when I say that? Well, out of the box inside of Foundry, we have a number of built-in evaluators. There's one that can evaluate tool selection, tool output, tool input, retrieval evaluation, fluency evaluator.

Sometimes I look at this list, though, and I get a little bit overwhelmed, right? My agent is this field operation spacing agent. What's the right combination of built-in evaluators? Well, the answer is actually you might even sometimes want a custom rubric. So this will actually go through and help you generate the right combination of evaluators for your specific agent. So once I do that, this will initialize my project. Let's actually show you the custom rubric that this generated for my agent.

So you can see here this isn't just a single dimension, this is actually used in LLM to suggest for me a few different dimensions that it recognizes are likely important. So it said, "Hey, you probably want to make sure that it is calling the right tools." When I ask about uptime, I want to make sure I'm using Fabric IQ. So let's make the highest-weighted thing correct tool use. Safety warning is probably a big one, right, like this is custom unique to me, this is now personalized for my specific agent. Now, I can modify this, too. In this case, you can see it actually suggested this voice-optimized conciseness.

Right now it gives this a weight of three. Based on the feedback that I'm hearing, I actually want to bump that up to 10. I want it to weigh much more heavily on making sure that this thing is voice-optimized based on the feedback that I've gotten. So I can go ahead and update this evaluator so that now it is doing voice optimized in that custom rubric. So now I have this personalized evaluator for my specific scenario that's looking at these pieces. And again, I can modify this and customize this as I need.

Now, where do I go from here? Well, I have my dataset. So this is the dataset that I had used to generate ahead of time.

This has a few questions that people might ask, as well as some answers. And now I have my custom evaluator. And I can pull them altogether now with what is probably my favorite CLI command in the world, which is "azd ai agent optimize". Now, let me walk you through what optimize is going to do. I'm going to choose this agent that says, "Hey, you've already initialized this for evaluations. You want to use that configuration." So what this is going to do is it says, "Okay, I see the system prompts, the instructions that this agent has, the instructions that you gave it in its code. I see any skills that you might have configured for this agent to have. I see the tool configuration that you have." I can even look at things like the target model.

Am I using GPT-5.5, am I using Anthropic, Opus 4.8? Do I want to use that as a variable?" I can specify what are the variables that I want to have, and then here I'm going to choose a model to help drive the optimization process. I'm just going to leave this at GPT-5 right now. Now, what this kicks off for me -- this will actually take a while, this kicks off an automatic optimization loop. This is going to go through and adjust all of those different variables. It's going to say, "Okay, what if I modify your system prompts?

What if I modify your tool descriptions? What if we use a different model?" This is going to use leading data science techniques to go find some potential candidates for better versions of my agent based on my custom rubric that we defined. Now, rather than us waiting here for the next however long this takes, a couple dozen minutes, let's actually just jump ahead quickly to where I have -- oh my desktops are all out of whack. Let's see if we can find this one.

Everyone cross your fingers. It's here somewhere. Oh, you know where it was, it was in Chrome that I closed earlier. Okay.

Hold on. It's here. It's here. Nobody doubt that it is here.

Where is it? Oh, no. Okay, well, I have the URLs here in a second if need to use it, that Chrome thing before it threw me out. Okay, watch this. Live demo, live demo gods, please be on our side for this last piece. All right, let me copy this URL, paste it in here, and we'll let this load up.

Okay, so this -- aye, it's live. Okay, so this is the evaluation that I ran a little bit ago. You can see it ran through and it said, "Hey, we actually found a candidate that will boost your evaluator 11%." You will get 11% better performance, just by me sitting and waiting for that thing to finish. You can see here it actually identified four candidates.

Each of them had different pros and cons. If I want to, I can understand, "Well, what did you change?" You can see here, "Hey, this was your existing system prompt. Here's a new system prompt that if you use this system prompt, you actually get better behavior." So I can go ahead and dive into the results. I can dive really deep in to all of the score details

all of those eval sets that it tested against and once I'm ready to go I can go ahead now and deploy this as the new version of my agent and make this candidate the default candidate so I get that improvement on voice conciseness. So all of this loop we were able to use AI to automatically power a bunch of that for me just running this optimization loop. That's the same power we want to put into all of your hands as you're building your agents.

So with that, Tina will bring it on out to wrap things up.

**Tina Schuchman:** Thank you, Jeff. Now let's recap on operate. Creating an evaluation for hosted agents is generally available soon. Every single LLM call, tool invocation, sub-second hub handoff is all logged in one open telemetry pipeline. Rubric for custom evaluation is now in public preview.

Rubric autogenerates context of where criteria and weighted scoring to define what good looks like for both evaluation and optimization so the developer doesn't have to start from scratch. Agent Optimizer for Foundry Agent Service is now in private preview. Agent Optimizer turns production traces and evals into a set of ranked candidates by tweaking skills, prompts, tool configuration, and even models. These ranked candidates are then shown side-by-side across quality, cost, and latency, that you developer are in control to choose the exact winning variant to promote, with fold, traceback, and lineage.

Rollback is right there when you need it. The platform finds optimization developers in control on every single change. Procedural memory in Foundry Agent Service is now in public preview. Procedural memory empowers the agent to learn the playbook across all sessions so the agent doesn't have to start learning from scratch in every single conversation.

As you can see, there is no manual rewrite, or prompt, or skills. The agent becomes smarter, safer, and cheaper the more advanced, always developer in control for every single change. So let me now close out what that all means. This is not just a roadmap promise. Over 80,000 customers are running on Foundry today and they are already taking advantage of production agents driving significant business outcomes.

Iberdrola is scaling their mission critical energy operations across 14 countries. They are leveraging identity, memory, governance, observability, all right from the Foundry Agent Service, with full control over regulated operations. Twilio has deployed the Twilio Agent Connect, which is their open-source framework that connects AI agents with the Twilio platform, all running on hosted agents in Foundry. KPMG is building their global KPMG workbench platform on hosted agents. They are leveraging tools and skills in Foundry Toolbox, supercharging their interaction with clients worldwide.

Now let's recap on what just happened in the last 45 minutes. We started with a scenario our Azure networking operations team faces on a daily basis. A fiber got cut near one of our data centers. We then built an agent locally with Microsoft Agent Framework as the orchestrator. We connected to the Foundry Toolbox, Foundry IQ, memory, voice, Document Intelligence and Content Understanding. We then hosted as a hosted agent so it runs in a isolated secure execution runtime.

We then published into Teams as a Copilot agent. We then operated the agent that works autonomously, traced end-to-end covering production, and is meaningfully getting better through every single run. This is the power of Microsoft Foundry seamless hosting connected intelligence

enterprise trust and reach all in one runtime so super easy for you to scale your locally scaffolded agent from your laptop to scale through thousands of conversations running in production. This is Microsoft Foundry, built simply, deployed powerfully, operate with trust. That's the promise we just walked you through and is available to every single developer in this room today. Here are a few sessions that you may want to check out at Build.

**\[ Applause** \]

I am super excited to see what you can build with Microsoft Foundry. Thank you.

Have a great build.

**Jeff Hollan:** Thanks, everyone. We'll stick -- we have about five minutes where we can come down here if anyone has any questions. If we're not able to answer your question before the next session, which you should stick around for -- I think it's on observability, the Foundry booth is just back here and we've got the team here all week. So we'll answer what we can here, and yeah, thanks so much for coming, everyone.

**\[ Music** \]

END
