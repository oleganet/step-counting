# step-counting
import React, { useState } from 'react';
import { Progress } from '@/components/ui/progress';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';

export default function StepCounter() {
    const [steps, setSteps] = useState(0);
    const [goal, setGoal] = useState(10000);
    const [input, setInput] = useState('');

    const handleAddSteps = () => {
        const newSteps = parseInt(input, 10);
        if (!isNaN(newSteps) && newSteps > 0) {
            setSteps(prev => prev + newSteps);
            setInput('');
        }
    };

    const handleReset = () => {
        setSteps(0);
    };

    return (
        <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100 p-4">
            <div className="bg-white rounded-2xl shadow-xl p-6 w-full max-w-sm">
                <h1 className="text-2xl font-bold mb-4 text-center">Step Counter</h1>
                <p className="text-lg mb-2 text-center">Today's Steps: <span className="font-semibold">{steps}</span></p>
                <Progress value={(steps / goal) * 100} className="mb-4" />
                <div className="flex gap-2 mb-4">
                    <Input 
                        type="number" 
                        value={input} 
                        onChange={(e) => setInput(e.target.value)} 
                        placeholder="Add steps" 
                        className="flex-1" 
                    />
                    <Button onClick={handleAddSteps}>Add</Button>
                </div>
                <Button onClick={handleReset} variant="secondary" className="w-full">Reset</Button>
            </div>
        </div>
67
