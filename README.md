# -
用于增强学生学习近代史的兴趣
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>马克思主义答题挑战</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 10px;
            color: #333;
            overflow: hidden; /* 防止烟花效果导致滚动条出现 */
        }

        .container {
            max-width: 400px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            min-height: 90vh;
            position: relative; /* 为内部绝对定位元素提供参照 */
            z-index: 10;
        }

        .header {
            text-align: center;
            margin-bottom: 20px;
            padding: 20px 0;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            border-radius: 15px;
            color: white;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .header h1 {
            font-size: 24px;
            margin-bottom: 10px;
        }

        .score-board {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            padding: 15px;
            background: linear-gradient(45deg, #ffeaa7, #fdcb6e);
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }

        .score-item {
            text-align: center;
            flex: 1;
        }

        .score-item h3 {
            font-size: 18px;
            color: #2d3436;
            margin-bottom: 5px;
        }

        .score-item p {
            font-size: 16px;
            font-weight: bold;
            color: #e17055;
        }

        .question-container {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            border-left: 5px solid #74b9ff;
        }

        .question-number {
            font-size: 14px;
            color: #636e72;
            margin-bottom: 10px;
        }

        .question-text {
            font-size: 18px;
            line-height: 1.6;
            color: #2d3436;
            margin-bottom: 20px;
            font-weight: 500;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .option {
            padding: 15px;
            background: #f8f9fa;
            border: 2px solid #e9ecef;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 16px;
            color: #495057;
        }

        .option:hover {
            background: #e3f2fd;
            border-color: #2196f3;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(33, 150, 243, 0.2);
        }

        .option.selected {
            background: #2196f3;
            color: white;
            border-color: #1976d2;
        }

        .option.correct {
            background: #4caf50;
            color: white;
            border-color: #388e3c;
        }

        .option.incorrect {
            background: #f44336;
            color: white;
            border-color: #d32f2f;
        }

        .submit-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 20px;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .submit-btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }

        .result {
            text-align: center;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            font-size: 16px;
            font-weight: bold;
        }

        .result.correct {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .result.incorrect {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        .coin-reward {
            display: inline-block;
            background: #ffd700;
            color: #856404;
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 14px;
            margin-top: 10px;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: #e9ecef;
            border-radius: 4px;
            margin-bottom: 20px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea, #764ba2);
            border-radius: 4px;
            transition: width 0.3s ease;
        }

        .start-screen {
            text-align: center;
            padding: 40px 20px;
        }

        .start-screen h2 {
            color: #2d3436;
            margin-bottom: 20px;
            font-size: 24px;
        }

        .start-screen p {
            color: #636e72;
            margin-bottom: 30px;
            font-size: 16px;
            line-height: 1.6;
        }

        .start-btn {
            background: linear-gradient(45deg, #00b894, #00cec9);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .start-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 184, 148, 0.4);
        }

        .final-screen {
            text-align: center;
            padding: 40px 20px;
        }
        
        #fireworks-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1; /* 确保在背景和内容之间 */
            display: none; /* 默认隐藏 */
        }
        
        .final-screen h2 {
            color: #2d3436;
            margin-bottom: 20px;
            font-size: 28px;
        }
        
        #surpriseMessage {
            color: #d63031;
            font-weight: bold;
            margin-bottom: 15px;
            display: none; /* 默认隐藏 */
        }

        .final-stats {
            background: rgba(248, 249, 250, 0.9);
            border-radius: 15px;
            padding: 20px;
            margin: 20px 0;
            position: relative;
            z-index: 20;
        }

        .final-stats p {
            margin: 10px 0;
            font-size: 16px;
            color: #495057;
        }

        .restart-btn {
            background: linear-gradient(45deg, #fd79a8, #fdcb6e);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .restart-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(253, 121, 168, 0.4);
        }

        @media (max-width: 480px) {
            .container {
                margin: 5px;
                padding: 15px;
                min-height: 95vh;
            }

            .question-text {
                font-size: 16px;
            }

            .option {
                padding: 12px;
                font-size: 14px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎓 马克思主义答题挑战</h1>
            <p>测试你的马克思主义理论知识</p>
        </div>

        <div id="startScreen" class="start-screen">
            <h2>欢迎参加答题挑战！</h2>
            <p>本次挑战共50题，难度将逐渐提升。答对可获得金币，累计金币有惊喜哦！准备好开始你的学习之旅了吗？</p>
            <button class="start-btn" onclick="startQuiz()">开始答题</button>
        </div>

        <div id="gameScreen" style="display: none;">
            <div class="score-board">
                <div class="score-item">
                    <h3>金币</h3>
                    <p id="coins">0</p>
                </div>
                <div class="score-item">
                    <h3>进度</h3>
                    <p><span id="currentProgress">0</span> / <span id="totalProgress">50</span></p>
                </div>
                <div class="score-item">
                    <h3>答对</h3>
                    <p id="correct">0</p>
                </div>
            </div>

            <div class="progress-bar">
                <div class="progress-fill" id="progressFill"></div>
            </div>

            <div class="question-container">
                <div class="question-number" id="questionNumber">第 1 题</div>
                <div class="question-text" id="questionText">题目加载中...</div>
                <div class="options" id="options"></div>
            </div>

            <button class="submit-btn" id="submitBtn" onclick="submitAnswer()" disabled>请选择答案</button>

            <div id="result" class="result" style="display: none;"></div>
        </div>

        <div id="finalScreen" class="final-screen" style="display: none;">
            <h2>🎉 挑战完成！</h2>
            <p id="surpriseMessage">恭喜！金币达成特定目标，为你送上惊喜！</p>
            <div class="final-stats">
                <p><strong>总金币：</strong><span id="finalCoins">0</span></p>
                <p><strong>答对题目：</strong><span id="finalCorrect">0</span></p>
                <p><strong>总题数：</strong><span id="finalTotal">0</span></p>
                <p><strong>正确率：</strong><span id="accuracy">0%</span></p>
            </div>
            <button class="restart-btn" onclick="restartQuiz()">重新开始</button>
        </div>
    </div>
    
    <canvas id="fireworks-canvas"></canvas>

    <script>
        // 烟花效果的JS代码 (一个轻量级的实现)
        const fireworks = (function() {
            const canvas = document.getElementById('fireworks-canvas');
            const ctx = canvas.getContext('2d');
            let sparks = [];
            let fireworks = [];
            let running = false;
            let timeout;

            function Spark(x, y, vx, vy, color) {
                this.x = x; this.y = y; this.vx = vx; this.vy = vy;
                this.color = color; this.alpha = 1;
            }

            Spark.prototype.draw = function() {
                ctx.globalAlpha = this.alpha;
                ctx.fillStyle = this.color;
                ctx.fillRect(this.x, this.y, 2, 2);
            };

            Spark.prototype.update = function() {
                this.x += this.vx; this.y += this.vy;
                this.vy += 0.03; // gravity
                this.alpha -= 0.02;
            };

            function Firework(x, y, tx, ty) {
                this.x = x; this.y = y; this.tx = tx; this.ty = ty;
                const dx = tx - x, dy = ty - y;
                this.dist = Math.sqrt(dx * dx + dy * dy);
                const angle = Math.atan2(dy, dx);
                this.vx = Math.cos(angle) * 4;
                this.vy = Math.sin(angle) * 4;
            }

            Firework.prototype.draw = function() {
                ctx.fillStyle = 'white';
                ctx.fillRect(this.x, this.y, 3, 3);
            };

            Firework.prototype.update = function(index) {
                this.x += this.vx; this.y += this.vy;
                const dx = this.tx - this.x, dy = this.ty - this.y;
                if (Math.sqrt(dx * dx + dy * dy) < 5) {
                    explode(this.x, this.y);
                    fireworks.splice(index, 1);
                }
            };
            
            function explode(x, y) {
                const count = 100;
                const color = `hsl(${Math.random() * 360}, 100%, 50%)`;
                for (let i = 0; i < count; i++) {
                    const angle = Math.random() * Math.PI * 2;
                    const speed = Math.random() * 4;
                    sparks.push(new Spark(x, y, Math.cos(angle) * speed, Math.sin(angle) * speed, color));
                }
            }
            
            function loop() {
                if (!running) return;
                ctx.globalAlpha = 0.1;
                ctx.fillStyle = '#000';
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                ctx.globalAlpha = 1;

                for (let i = sparks.length - 1; i >= 0; i--) {
                    sparks[i].draw();
                    sparks[i].update();
                    if (sparks[i].alpha <= 0) sparks.splice(i, 1);
                }
                
                for (let i = fireworks.length - 1; i >= 0; i--) {
                    fireworks[i].draw();
                    fireworks[i].update(i);
                }

                requestAnimationFrame(loop);
            }
            
            function launch() {
                if(fireworks.length < 10) { // Limit number of fireworks
                   fireworks.push(new Firework(Math.random() * canvas.width, canvas.height, Math.random() * canvas.width, Math.random() * canvas.height / 2));
                }
            }

            return {
                start: function() {
                    if (running) return;
                    running = true;
                    canvas.style.display = 'block';
                    canvas.width = window.innerWidth;
                    canvas.height = window.innerHeight;
                    loop();
                    timeout = setInterval(launch, 800);
                },
                stop: function() {
                    running = false;
                    canvas.style.display = 'none';
                    sparks = [];
                    fireworks = [];
                    clearInterval(timeout);
                    ctx.clearRect(0, 0, canvas.width, canvas.height);
                }
            };
        })();

        // ===================================
        // 游戏核心逻辑
        // ===================================

        // 示例题库 - 您可以在这里添加更多题目，总量建议接近1000道。
        // difficulty: 1 (简单), 2 (中等), 3 (困难)
        const questionBank = [
             // 简单 (20题)
            { question: "马克思主义的理论来源不包括以下哪项？", options: ["德国古典哲学", "英国古典政治经济学", "法国空想社会主义", "美国实用主义"], correct: 3, explanation: "马克思主义的理论来源主要是德国古典哲学、英国古典政治经济学和法国空想社会主义。", difficulty: 1 },
            { question: "物质的唯一特性是什么？", options: ["运动性", "客观实在性", "可知性", "发展性"], correct: 1, explanation: "客观实在性是物质的唯一特性，它不依赖于人的主观意识而存在。", difficulty: 1 },
            { question: "商品的二重性是指？", options: ["使用价值和价值", "具体劳动和抽象劳动", "私人劳动和社会劳动", "必要劳动和剩余劳动"], correct: 0, explanation: "商品的二重性是指使用价值和价值，这是商品的两个基本属性。", difficulty: 1 },
            { question: "马克思主义最鲜明的品格是什么？", options: ["科学性", "革命性", "人民性", "实践性"], correct: 3, explanation: "实践性是马克思主义最鲜明的品格，它强调理论与实践的统一。", difficulty: 1 },
            { question: "社会主义的根本任务是？", options: ["消灭剥削", "解放生产力，发展生产力", "实现共同富裕", "建设和谐社会"], correct: 1, explanation: "解放生产力，发展生产力是社会主义的根本任务，这是社会主义建设的核心。", difficulty: 1 },
            { question: "马克思主义哲学的基本问题是？", options: ["物质和意识的关系问题", "理论和实践的关系问题", "认识和实践的关系问题", "存在和思维的关系问题"], correct: 3, explanation: "存在和思维的关系问题是马克思主义哲学的基本问题，也是整个哲学的基本问题。", difficulty: 1 },
            { question: "认识的本质是？", options: ["主体对客体的反映", "主体对客体的能动反映", "客体对主体的作用", "主体的主观创造"], correct: 1, explanation: "认识的本质是主体对客体的能动反映，强调认识既是反映又是能动的。", difficulty: 1 },
            { question: "真理和谬误的关系是？", options: ["绝对对立", "相互转化", "既对立又统一", "没有关系"], correct: 2, explanation: "真理和谬误既对立又统一，在一定条件下可以相互转化。", difficulty: 1 },
            { question: "人民群众是历史的创造者，这一观点强调的是？", options: ["人民群众的主观能动性", "人民群众在历史发展中的决定作用", "人民群众是历史活动的主体", "人民群众的革命觉悟"], correct: 2, explanation: "人民群众是历史的创造者强调人民群众是历史活动的主体，是推动历史发展的根本力量。", difficulty: 1 },
            { question: "马克思主义政治经济学的研究对象是？", options: ["生产关系", "生产力", "经济规律", "社会生产关系及其发展规律"], correct: 3, explanation: "马克思主义政治经济学的研究对象是社会生产关系及其发展规律。", difficulty: 1 },
            { question: "无产阶级革命的最高形式是？", options: ["经济斗争", "政治斗争", "武装斗争", "思想斗争"], correct: 2, explanation: "武装斗争是无产阶级革命的最高形式，是夺取政权的根本途径。", difficulty: 1 },
            { question: "“纸上得来终觉浅，绝知此事要躬行”体现的哲学道理是？", options: ["物质决定意识", "实践是认识的来源", "矛盾的普遍性", "量变引起质变"], correct: 1, explanation: "这句诗强调了亲身实践的重要性，说明实践是获得真知的根本途径。", difficulty: 1 },
            { question: "划分唯物主义和唯心主义的唯一标准是？", options: ["对物质和意识哪个是第一性的回答", "对世界是否可知晓的回答", "对世界是运动还是静止的回答", "对社会存在和社会意识关系的回答"], correct: 0, explanation: "承认物质是第一性、意识是第二性的就是唯物主义；反之则是唯心主义。", difficulty: 1 },
            { question: "资本主义生产过程是？", options: ["劳动过程和价值形成过程的统一", "劳动过程和价值增殖过程的统一", "价值形成过程和价值增殖过程的统一", "劳动过程和使用价值生产过程的统一"], correct: 1, explanation: "资本主义生产不仅要生产出价值，更要生产出剩余价值，因此是劳动过程和价值增殖过程的统一。", difficulty: 1 },
            { question: "空想社会主义的代表人不包括？", options: ["圣西门", "傅立叶", "欧文", "马克思"], correct: 3, explanation: "马克思是科学社会主义的创始人，而不是空想社会主义者。", difficulty: 1 },
            { question: "世界的统一性在于它的？", options: ["多样性", "运动性", "物质性", "可知性"], correct: 2, explanation: "马克思主义哲学认为，世界是统一的，其统一性在于它的物质性。", difficulty: 1 },
            { question: "社会发展的最终决定力量是？", options: ["人口因素", "地理环境", "生产方式", "文化传统"], correct: 2, explanation: "生产方式，即生产力和生产关系的统一体，是社会发展的最终决定力量。", difficulty: 1 },
            { question: "货币的本质是？", options: ["商品", "金银", "一般等价物", "劳动产品"], correct: 2, explanation: "货币是从商品中分离出来，固定地充当一般等价物的特殊商品。", difficulty: 1 },
            { question: "阶级斗争的根源在于？", options: ["思想观念的对立", "物质利益的对立", "政治主张的不同", "生活方式的差异"], correct: 1, explanation: "阶级斗争是阶级社会中经济利益根本对立的阶级之间的对抗和冲突。", difficulty: 1 },
            { question: "共产主义社会的第一阶段是？", options: ["资本主义社会", "社会主义社会", "新民主主义社会", "过渡时期"], correct: 1, explanation: "马克思和恩格斯把共产主义社会划分为第一阶段（社会主义）和高级阶段（共产主义）。", difficulty: 1 },

            // 中等 (20题)
            { question: "实践是检验真理的唯一标准，这一观点体现了？", options: ["真理的客观性", "真理的绝对性", "真理的相对性", "真理的具体性"], correct: 0, explanation: "实践是检验真理的唯一标准体现了真理的客观性，因为实践是客观的物质活动。", difficulty: 2 },
            { question: "马克思主义认为，推动社会历史发展的根本动力是？", options: ["生产力", "生产关系", "社会基本矛盾", "阶级斗争"], correct: 2, explanation: "社会基本矛盾（生产力与生产关系、经济基础与上层建筑的矛盾）是推动社会历史发展的根本动力。", difficulty: 2 },
            { question: "剩余价值的源泉是？", options: ["不变资本", "可变资本", "劳动力商品的使用价值", "机器设备"], correct: 2, explanation: "剩余价值的源泉是劳动力商品的使用价值，即劳动力在生产过程中创造的超过自身价值的价值。", difficulty: 2 },
            { question: "“从物到感觉和思想”与“从思想和感觉到物”是两条根本对立的认识路线，它们分别属于？", options: ["辩证法与形而上学", "唯物主义与唯心主义", "可知论与不可知论", "一元论与二元论"], correct: 1, explanation: "前者是唯物主义的认识路线，后者是唯心主义的认识路线。", difficulty: 2 },
            { question: "资本区分为不变资本和可变资本的依据是？", options: ["它们在价值增殖过程中的不同作用", "它们在生产中的物质形态不同", "它们的价值周转方式不同", "它们是否存在于流通领域"], correct: 0, explanation: "不变资本不带来价值增殖，可变资本（用于购买劳动力）是剩余价值的源泉。", difficulty: 2 },
            { question: "经济基础是指？", options: ["生产力", "由一定发展阶段的生产力所决定的生产关系的总和", "社会上层建筑", "国家的政治制度和法律制度"], correct: 1, explanation: "经济基础是与生产力发展的一定阶段相适应的生产关系的总和。", difficulty: 2 },
            { question: "“时势造英雄”和“英雄造时势”这两种观点分别属于？", options: ["历史唯物主义和历史唯心主义", "辩证法和形而上学", "唯物论和唯心论", "可知论和不可知论"], correct: 0, explanation: "“时势造英雄”是历史唯物主义观点，承认社会发展有其客观规律；“英雄造时势”是历史唯心主义观点，夸大个人作用。", difficulty: 2 },
            { question: "绝对剩余价值生产和相对剩余价值生产的共同点是？", options: ["都缩短了必要劳动时间", "都延长了剩余劳动时间", "都提高了劳动生产率", "都改变了工作日的长度"], correct: 1, explanation: "两种方法都旨在延长工人创造剩余价值的时间，从而提高剥削程度。", difficulty: 2 },
            { question: "社会主义民主的本质和核心是？", options: ["人民当家作主", "党的领导", "依法治国", "少数服从多数"], correct: 0, explanation: "社会主义民主的本质是人民当家作主，这是它与一切剥削阶级民主的根本区别。", difficulty: 2 },
            { question: "辩证法的实质和核心是？", options: ["联系和发展的观点", "质量互变规律", "否定之否定规律", "对立统一规律"], correct: 3, explanation: "对立统一规律（矛盾规律）揭示了事物发展的源泉和动力，是辩证法的实质和核心。", difficulty: 2 },
            { question: "资本主义意识形态的核心是？", options: ["自由、平等、博爱", "拜金主义", "利己主义", "享乐主义"], correct: 2, explanation: "以私有制为基础的利己主义是资本主义意识形态的核心，它渗透到社会生活的各个方面。", difficulty: 2 },
            { question: "决定商品价值量的是？", options: ["商品的使用价值", "商品的供求关系", "生产商品的个别劳动时间", "生产商品的社会必要劳动时间"], correct: 3, explanation: "社会必要劳动时间决定商品的价值量，它是指在现有的社会正常的生产条件下，在社会平均的劳动熟练程度和劳动强度下制造某种使用价值所需要的劳动时间。", difficulty: 2 },
            { question: "社会意识相对独立性的最突出表现是它？", options: ["与社会存在发展具有不完全同步性", "具有历史继承性", "对社会存在具有能动的反作用", "各种形式之间相互影响"], correct: 2, explanation: "先进的社会意识对社会发展起积极的推动作用，落后的社会意识对社会发展起阻碍作用，这是其相对独立性的最突出表现。", difficulty: 2 },
            { question: "金融资本是由什么融合而成的？", options: ["工业资本和商业资本", "银行垄断资本和工业垄断资本", "生产资本和流通资本", "借贷资本和商品资本"], correct: 1, explanation: "金融资本是在垄断阶段，由银行垄断资本和工业垄断资本相互渗透、融合而形成的一种新型资本。", difficulty: 2 },
            { question: "人的本质在其现实性上是？", options: ["一切社会关系的总和", "自然属性和社会属性的统一", "人的主观意志", "人的自由"], correct: 0, explanation: "马克思认为，人的本质不是单个人所固有的抽象物，在其现实性上，它是一切社会关系的总和。", difficulty: 2 },
            { question: "国家是？", options: ["社会契约的产物", "阶级矛盾不可调和的产物和表现", "管理公共事务的机构", "超阶级的存在"], correct: 1, explanation: "国家是阶级统治的工具，是一个阶级镇压另一个阶级的暴力机关。", difficulty: 2 },
            { question: "劳动力成为商品的两个基本条件是？", options: ["劳动者有劳动能力，且没有生产资料", "劳动者有人身自由，且一无所有", "劳动者愿意出卖劳动力，且有市场", "劳动者掌握生产技术，且没有工作"], correct: 1, explanation: "劳动者必须有人身自由，能够自由支配自己的劳动力；同时他又必须丧失一切生产资料和生活资料，不得不出卖劳动力为生。", difficulty: 2 },
            { question: "“凡是现实的都是合乎理性的，凡是合乎理性的都是现实的。”这是谁的著名命题？", options: ["康德", "黑格尔", "费尔巴哈", "马克思"], correct: 1, explanation: "这是黑格尔的著名哲学命题，体现了他的唯心主义辩证法思想。", difficulty: 2 },
            { question: "价值规律的作用不包括？", options: ["自发地调节生产资料和劳动力在社会各生产部门之间的分配", "自发地刺激社会生产力的发展", "自发地导致商品生产者两极分化", "自发地消除贫富差距"], correct: 3, explanation: "价值规律在资本主义条件下会导致两极分化，即少数人暴富，多数人贫困，而不会消除贫富差距。", difficulty: 2 },
            { question: "在资本主义社会，工人的工资是？", options: ["劳动的价值或价格", "劳动力的价值或价格", "工人创造的全部价值", "工人付出的劳动量"], correct: 1, explanation: "工资在形式上表现为“劳动的价格”，但实质是劳动力的价值或价格。", difficulty: 2 },
            
            // 困难 (10题)
            { question: "马克思主义的根本观点是什么？", options: ["阶级斗争观点", "实践观点", "历史观点", "发展观点"], correct: 1, explanation: "实践观点是马克思主义的根本观点，是马克思主义哲学的核心和出发点。", difficulty: 3 },
            { question: "“全部社会生活在本质上是实践的”，这一观点出自？", options: ["《德意志意识形态》", "《资本论》", "《关于费尔巴哈的提纲》", "《共产党宣言》"], correct: 2, explanation: "马克思在《关于费尔巴哈的提纲》中提出：“凡是把理论引向神秘主义的神秘东西，都能在人的实践中以及对这个实践的理解中得到合理的解决。”并指出“全部社会生活在本质上是实践的。”", difficulty: 3 },
            { question: "资本主义地租的实质是？", options: ["土地所有者凭借土地所有权获得的收入", "农业工人创造的超过其劳动力价值的剩余价值的一部分", "土地的自然生产力的产物", "对土地投资所获得的回报"], correct: 1, explanation: "地租是农业资本家雇佣工人创造的剩余价值的一部分，是土地所有者凭借土地所有权无偿占有的部分。", difficulty: 3 },
            { question: "无产阶级专政的最终目标是？", options: ["建立社会主义公有制", "镇压剥削阶级的反抗", "发展社会生产力", "消灭阶级，实现无阶级社会"], correct: 3, explanation: "无产阶级专政是一个过渡时期，其历史任务是为消灭阶级、进入无阶级社会创造条件。", difficulty: 3 },
            { question: "抽象劳动和具体劳动的关系是？", options: ["同一劳动过程的两个方面", "两种不同的劳动", "先进行具体劳动，再进行抽象劳动", "对立统一的关系"], correct: 3, explanation: "任何一种劳动，一方面是特殊的、具体的劳动，创造商品的使用价值；另一方面又是无差别的一般人类劳动，形成商品的价值。二者是同一劳动过程的两个方面，是对立统一的关系。", difficulty: 3 },
            { question: "社会形态的发展是一种？", options: ["由人的主观意志决定的过程", "杂乱无章、没有规律的过程", "自然历史过程", "循环往复的过程"], correct: 2, explanation: "社会形态的更替是由社会基本矛盾运动决定的客观过程，像自然界演变一样有其不以人的意志为转移的客观规律，因此说它是一种自然历史过程。", difficulty: 3 },
            { question: "生产价格的构成是？", options: ["成本价格+利润", "不变资本+可变资本", "成本价格+平均利润", "可变资本+剩余价值"], correct: 2, explanation: "当利润转化为平均利润后，商品的价值就转化为生产价格，其公式为：生产价格=成本价格+平均利润。", difficulty: 3 },
            { question: "东方社会理论是谁提出的？", options: ["马克思、恩格斯", "列宁", "斯大林", "毛泽东"], correct: 0, explanation: "马克思、恩格斯在晚年研究了俄国等东方国家的社会发展道路，提出了跨越资本主义“卡夫丁峡谷”的设想，形成了东方社会理论。", difficulty: 3 },
            { question: "共产主义社会能够实现个人自由与社会必然性相统一的根本条件是？", options: ["生产力的高度发展", "人们思想觉悟的极大提高", "劳动不再是谋生的手段，而成为生活的第一需要", "国家的消亡"], correct: 0, explanation: "只有生产力高度发展，物质财富极大丰富，才能为每个人的全面自由发展提供坚实的物质基础，从而实现个人与社会的和谐统一。", difficulty: 3 },
            { question: "科学社会主义的核心内容是？", options: ["无产阶级专政和社会主义民主", "唯物史观和剩余价值学说", "国家学说", "人的全面发展学说"], correct: 0, explanation: "无产阶级专政和社会主义民主是科学社会主义的核心内容，是无产阶级革命胜利后建立和巩固新型社会制度的根本保证。", difficulty: 3 }
        ];

        const QUIZ_LENGTH = 50;
        // 注释: 答对40题以上(即获得400金币)会有惊喜烟花特效!
        const FIREWORKS_THRESHOLD = 400; 

        let currentQuestionIndex = 0;
        let score = 0;
        let correctAnswers = 0;
        let selectedAnswer = null;
        let gameQuestions = [];

        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }
        
        function startQuiz() {
            document.getElementById('startScreen').style.display = 'none';
            document.getElementById('finalScreen').style.display = 'none';
            document.getElementById('gameScreen').style.display = 'block';

            // 1. 按难度分离题库
            const easyQuestions = questionBank.filter(q => q.difficulty === 1);
            const mediumQuestions = questionBank.filter(q => q.difficulty === 2);
            const hardQuestions = questionBank.filter(q => q.difficulty === 3);

            // 2. 将各类题库随机打乱
            shuffleArray(easyQuestions);
            shuffleArray(mediumQuestions);
            shuffleArray(hardQuestions);

            // 3. 按20(易), 20(中), 10(难)的比例组合成50道题的考卷
            gameQuestions = [
                ...easyQuestions.slice(0, 20),
                ...mediumQuestions.slice(0, 20),
                ...hardQuestions.slice(0, 10)
            ];

            currentQuestionIndex = 0;
            score = 0;
            correctAnswers = 0;
            updateScoreBoard();
            showQuestion();
        }

        function showQuestion() {
            if (currentQuestionIndex >= QUIZ_LENGTH) {
                showFinalScreen();
                return;
            }

            const question = gameQuestions[currentQuestionIndex];
            document.getElementById('questionNumber').textContent = `第 ${currentQuestionIndex + 1} 题`;
            document.getElementById('questionText').textContent = question.question;

            const optionsContainer = document.getElementById('options');
            optionsContainer.innerHTML = '';

            question.options.forEach((option, index) => {
                const optionDiv = document.createElement('div');
                optionDiv.className = 'option';
                optionDiv.textContent = `${String.fromCharCode(65 + index)}. ${option}`;
                optionDiv.onclick = () => selectOption(index, optionDiv);
                optionsContainer.appendChild(optionDiv);
            });

            document.getElementById('submitBtn').disabled = true;
            document.getElementById('submitBtn').textContent = '请选择答案';
            document.getElementById('result').style.display = 'none';
            selectedAnswer = null;

            updateProgress();
        }

        function selectOption(index, element) {
            document.querySelectorAll('.option').forEach(opt => {
                opt.classList.remove('selected');
            });
            element.classList.add('selected');
            selectedAnswer = index;
            document.getElementById('submitBtn').disabled = false;
            document.getElementById('submitBtn').textContent = '确认答案';
        }

        function submitAnswer() {
            if (selectedAnswer === null) return;

            const question = gameQuestions[currentQuestionIndex];
            const isCorrect = selectedAnswer === question.correct;
            
            // 禁用所有选项的点击
            document.querySelectorAll('.option').forEach(opt => opt.onclick = null);

            const options = document.querySelectorAll('.option');
            options[question.correct].classList.add('correct');
            if (!isCorrect) {
                options[selectedAnswer].classList.add('incorrect');
            }

            const resultDiv = document.getElementById('result');
            if (isCorrect) {
                correctAnswers++;
                const coinReward = 10;
                score += coinReward;
                resultDiv.className = 'result correct';
                resultDiv.innerHTML = `
                    <div>🎉 回答正确！</div>
                    <div class="coin-reward">+${coinReward} 金币</div>
                    <div style="margin-top: 10px; font-size: 14px;">${question.explanation}</div>
                `;
            } else {
                resultDiv.className = 'result incorrect';
                resultDiv.innerHTML = `
                    <div>😔 回答错误</div>
                    <div style="margin-top: 10px; font-size: 14px;">正确答案：${String.fromCharCode(65 + question.correct)}. ${question.options[question.correct]}</div>
                    <div style="margin-top: 10px; font-size: 14px;">${question.explanation}</div>
                `;
            }

            resultDiv.style.display = 'block';
            updateScoreBoard();

            document.getElementById('submitBtn').textContent =
                currentQuestionIndex < QUIZ_LENGTH - 1 ? '下一题' : '完成答题';
            document.getElementById('submitBtn').onclick = nextQuestion;
        }

        function nextQuestion() {
            currentQuestionIndex++;
            document.getElementById('submitBtn').onclick = submitAnswer;
            showQuestion();
        }

        function updateScoreBoard() {
            document.getElementById('coins').textContent = score;
            document.getElementById('correct').textContent = correctAnswers;
            document.getElementById('currentProgress').textContent = currentQuestionIndex;
            document.getElementById('totalProgress').textContent = QUIZ_LENGTH;
        }

        function updateProgress() {
            const progress = (currentQuestionIndex / QUIZ_LENGTH) * 100;
            document.getElementById('progressFill').style.width = progress + '%';
            document.getElementById('currentProgress').textContent = currentQuestionIndex;
        }

        function showFinalScreen() {
            document.getElementById('gameScreen').style.display = 'none';
            document.getElementById('finalScreen').style.display = 'block';

            const accuracy = QUIZ_LENGTH > 0 ? Math.round((correctAnswers / QUIZ_LENGTH) * 100) : 0;
            document.getElementById('finalCoins').textContent = score;
            document.getElementById('finalCorrect').textContent = correctAnswers;
            document.getElementById('finalTotal').textContent = QUIZ_LENGTH;
            document.getElementById('accuracy').textContent = accuracy + '%';

            // 检查是否达到烟花阈值
            if (score >= FIREWORKS_THRESHOLD) {
                document.getElementById('surpriseMessage').style.display = 'block';
                fireworks.start();
            } else {
                 document.getElementById('surpriseMessage').style.display = 'none';
            }
        }

        function restartQuiz() {
            fireworks.stop(); // 停止烟花效果
            document.getElementById('finalScreen').style.display = 'none';
            document.getElementById('startScreen').style.display = 'block';
        }
        
        // 初始化
        document.getElementById('totalProgress').textContent = QUIZ_LENGTH;
    </script>
</body>
</html>
